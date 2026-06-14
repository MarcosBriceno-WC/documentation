---
name: api-endpoint-tester
description: >
  Use this skill when testing API endpoints with Bruno: scaffolding Bruno
  collection folders, executing requests, validating responses against the
  OpenAPI spec, identifying discrepancies, and keeping all supporting files
  and the Testing-Reports.md up to date with findings.
---

# API Endpoint Tester

You are testing API endpoints in a staging or sandbox environment using
Bruno. Your primary source of truth is the OpenAPI spec provided in this
project. Your secondary sources are the supporting files in
`references/`. Your output goes into the Bruno collection and into
`bruno-collection/Testing-Reports.md`.

> **Async endpoints:** Before testing any endpoint, check
> `supporting-files/async-endpoints.md`. If the endpoint is listed there,
> its primary payload arrives via webhook — a thin or empty HTTP response
> is correct behavior, not a failure. Do not flag it as broken. Webhook
> validation is handled by a separate companion skill.

> **Updating supporting files:** You are expected to update supporting
> files as you discover new information. This includes appending discovered
> discrepancies, correcting prerequisites, adding discovered workflows, and
> updating test references. Never silently discard a finding — write it
> down.

---

## Phase 1: Understand before you run

Before creating any Bruno files or executing any requests:

1. **Read the OpenAPI spec.** For the target endpoints, note the method,
   URL, required fields, field names, expected request body schema, and
   expected response schema and status code.

2. **Read all supporting files** in this order:
   - `api-config.md` — base URL, auth header, environment name
   - `async-endpoints.md` — confirm whether your target endpoint is async
   - `prerequisites.md` — identify any prior state or resource chain
     required before this endpoint can be called
   - `known-discrepancies.md` — check whether this endpoint already has
     documented field name or response schema differences
   - `workflows.md` — check whether the flow you are testing is already
     partially mapped
   - `test-references.md` — collect any test credentials, cards, or magic
     values you will need

3. **Read existing Bruno files** before writing new ones. Look at two or
   three existing `.yml` files in the collection to understand the local
   format conventions (indentation, header style, examples block structure).
   If no collection exists yet, proceed to Phase 2 to scaffold it.

4. **Read `bruno-collection/Testing-Reports.md`** to understand what has
   already been tested so you do not duplicate work or overwrite findings.

---

## Phase 2: Scaffold the Bruno collection (if it does not exist)

If `bruno-collection/` does not exist, create it before running any
requests.

### Minimum required structure

```
bruno-collection/
  environments/
    <env-name>.yml        # populated from api-config.md
  bruno.json             # Bruno collection metadata
  Testing-Reports.md     # starts empty, updated after each session
```

### `bruno.json`

```json
{
  "version": "1",
  "name": "<Project Name> API",
  "type": "collection"
}
```

### Environment file (`environments/<env-name>.yml`)

Populate from `api-config.md`. Use the exact environment name specified
there so `bru run --env "<env-name>"` works.

```yaml
name: <env-name>
variables:
  - name: base_url
    value: <base_url from api-config.md>
    enabled: true
  - name: api_key
    value: <api_key from api-config.md>
    enabled: true
  # Add any additional variables defined in api-config.md
```

### Initial `Testing-Reports.md`

```markdown
# Testing Reports

## Session Log

<!-- Append a new session entry after each testing session. -->
```

---

## Phase 3: Bruno file conventions

### Folder naming

```
NN-ResourceName/
```

Where `NN` is the next available two-digit sequence number (for example,
`01-Charges/`, `02-Customers/`). Use the resource name as it appears in
the OpenAPI spec's tag or path group.

### File naming

Use readable English names ending in `.yml`:
- Simple endpoint: `Get a Charge.yml`, `List Customers.yml`
- Prerequisite chain: prefix with `Step N - `:
  `Step 1 - Create a Customer.yml`, `Step 2 - Create a Charge.yml`

### Folder metadata file (`folder.yml`)

```yaml
info:
  name: NN-ResourceName
  type: folder
  seq: <N>

request:
  auth: inherit
```

### Request file structure

```yaml
info:
  name: <Endpoint Name>
  type: http
  seq: <N>

# What this endpoint does.
# Prerequisites: <list any required prior state>
# Required fields: <list required request fields>
# Key response fields: <list important fields in the response>
# Spec notes: <any known differences from the OpenAPI spec>

http:
  method: <METHOD>
  url: "{{base_url}}/<path>/REPLACE_WITH_<RESOURCE>_ID"
  headers:
    - name: accept
      value: application/json
    - name: <auth-header-name from api-config.md>
      value: "{{api_key}}"
  # For POST/PUT/PATCH, add:
  # body:
  #   type: json
  #   data: |-
  #     { ... }

settings:
  encodeUrl: true
  timeout: 0
  followRedirects: true
  maxRedirects: 5

examples:
  - name: <Endpoint Name>
    request:
      url: "{{base_url}}/<path>/<real-id-from-test-run>"
      method: <METHOD>
      headers:
        - name: accept
          value: application/json
        - name: <auth-header-name>
          value: "{{api_key}}"
    response:
      status: <actual status code>
      statusText: <actual status text>
      headers:
        - name: content-type
          value: application/json; charset=utf-8
      body:
        type: json
        data: |-
          { ... actual response from the live API ... }
```

**Key rules:**
- The `http` block uses `REPLACE_WITH_...` placeholder IDs.
- The `examples` block uses real IDs from actual test runs.
- Use `"{{$randomUUID}}"` for idempotency keys in the base request. Use a
  fixed UUID string in examples.
- Always include `content-type: application/json` on requests with a body.
- Trim long nested objects in response bodies to the essential fields.
- The comment block at the top of each file is required — it is the
  primary human-readable documentation for that endpoint.

---

## Phase 4: Install and run Bruno

### Install Bruno CLI (if missing)

```bash
npm install -g @usebruno/cli
bru --version
```

### Run a single file

```bash
cd bruno-collection
bru run "01-Charges/Get a Charge.yml" --env "<env-name from api-config.md>"
```

### Run an entire folder

```bash
cd bruno-collection
bru run "01-Charges/" --env "<env-name from api-config.md>"
```

### Capture JSON output

```bash
bru run "01-Charges/Create a Charge.yml" \
  --env "<env-name>" --output json
cat json | python3 -c \
  "import json,sys; print(json.load(sys.stdin)[0]['results'][0]['response']['data']['id'])"
```

### Expected behavior with placeholder IDs

When running a whole folder, files with `REPLACE_WITH_...` placeholder IDs
will return 400 errors. This is expected — Bruno still marks them as
passed (a response was received). The tested data lives in the `examples`
blocks. Always validate individual endpoints with real IDs via `curl`
before writing the `examples` block.

### Using curl for exploratory calls

```bash
curl -s -X POST "<base_url>/<path>" \
  -H "<auth-header-name>: <api_key>" \
  -H "content-type: application/json" \
  -d '{ ... }' \
  -w "\nHTTP_STATUS:%{http_code}" | python3 -m json.tool
```

The `-w "\nHTTP_STATUS:%{http_code}"` flag appends the HTTP status code
after the body so you can read it separately from the response JSON.

For idempotency keys when using curl:

```bash
cat /proc/sys/kernel/random/uuid
```

---

## Phase 5: Diagnosing errors

### 400 Bad Request

1. Read the `message` and `params` (or equivalent error detail fields) in
   the response body. They typically name the exact invalid or missing
   field.
2. Cross-reference with the OpenAPI spec. If the spec field name differs
   from what the API reports, the spec is wrong.
3. Check `known-discrepancies.md` — this may already be documented.
4. Try the corrected request before updating any files.
5. If it was an undocumented discrepancy, append it to the **Discovered**
   section of `known-discrepancies.md`.

### 404 Not Found on a known resource

1. Confirm the ID format is correct (check `prerequisites.md` for
   expected ID prefixes).
2. Confirm the resource was created using the same API key and environment.
3. Check whether the resource requires a multi-step creation flow (for
   example, create then activate/upload). Consult `prerequisites.md`.

### Idempotency conflict

If reusing the same idempotency key for a different payload produces an
error, generate a new UUID. Do not retry with the same key.

### Unexpected thin or empty response

Before flagging as a bug, check `async-endpoints.md`. If the endpoint is
listed there, an empty or minimal HTTP response is correct — the payload
arrives via webhook.

### Stop condition

Stop and report to the user if:

- The same endpoint returns unexpected errors on three successive attempts
  with different valid inputs.
- An endpoint requires permissions not enabled on the test account
  (indicated by a `permission_denied` or `forbidden` error).
- A required upstream resource cannot be created due to a persistent API
  error blocking all dependent tests.

Do not retry the same failing request repeatedly. Change the approach,
consult `prerequisites.md`, or stop and report.

---

## Phase 6: Status transitions

Many APIs only allow certain operations when a resource is in a specific
status. Always check the current resource status before running an endpoint
that modifies state. Document any status transition rules you discover in
`prerequisites.md` under the relevant endpoint group.

When you need a fresh resource in a specific state, create a new one
rather than trying to reset an existing one.

---

## Phase 7: What to update after each test

### Bruno collection files

For each tested endpoint:

1. Create or update the `.yml` file with the validated request in the
   `http` block and the real response in an `examples` entry.
2. Ensure the comment block at the top of the file is accurate and
   complete.
3. Run the full folder with `bru run` and confirm all files receive a
   response.

### OpenAPI spec

Update the spec when you find:

- **Wrong field name** in request body — fix the property name and inline
  example.
- **Wrong response schema** — update the `$ref` or response description.
- **Wrong HTTP status code** — change the response key.
- **Missing required fields** — add a `required:` array to the request
  schema.

Always verify your spec edit does not introduce YAML syntax errors by
reviewing the changed section after editing.

### Supporting files — update rules

| File | When to update |
|---|---|
| `api-config.md` | New environment variables discovered during testing |
| `test-references.md` | New test values, magic IDs, or staging-only endpoints found |
| `prerequisites.md` | New resource chains, status transition rules, or corrected sequences |
| `known-discrepancies.md` | Any new spec vs. reality gap found during testing (append to Discovered section) |
| `async-endpoints.md` | Any endpoint confirmed to be async that was not already listed |
| `workflows.md` | Move a Discovered workflow to Known after author validation; add newly found flows to Discovered |

### Testing-Reports.md

After each testing session, append a new entry:

```markdown
## Session: <YYYY-MM-DD> — <Resource or Flow Name>

**Endpoints tested:** <list>
**Workflows validated:** <list workflow names from workflows.md>
**Discrepancies found:** <summary or "none">
**Spec updates made:** <list of changes or "none">
**Open questions:** <anything that needs follow-up>
```