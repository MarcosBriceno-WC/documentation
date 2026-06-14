# Prerequisites

> **How to use this file:** Document any state that must exist before an
> endpoint can be called successfully. This includes resource creation
> chains, required resource statuses, and multi-step setup flows. Seed
> this file from client briefings or API documentation before testing.
> The skill appends new chains and status transition rules as they are
> discovered during testing.

---

## Resource Chains

List endpoint groups that require prior resources to exist before they
can be tested. Use the format below and add a section per resource group.

---

### Template

```
## <Resource Group Name>

**Depends on:** <list of resource types that must exist first>

**Creation order:**
1. <Step 1: endpoint and what it creates>
2. <Step 2: endpoint and what it creates>
3. <Target endpoint>

**Notes:**
- <Any important caveats, for example: the upstream resource must be in
  a specific status>
```

---

<!-- Add your resource chain sections below this line. -->

---

## Status Transition Rules

Document any cases where an endpoint only works when a resource is in a
specific status, and what transitions move it out of that status.

| Resource | Operation | Required status | Resulting status | Notes |
|---|---|---|---|---|
| | | | | |

---

## Multi-step Setup Flows

Some resources require more than one API call to become usable (for
example, create then activate, or create then upload content). Document
these here.

---

### Template

```
### <Resource Type> — <Flow Name>

**Step 1:** `POST /<path>` — creates the record, returns `{ "id": "..." }`
**Step 2:** `POST /<path>/{id}/<action>` — activates or populates it
**Result:** Resource is now usable in subsequent requests

**What happens if Step 2 is skipped:**
<Describe the error the API returns when Step 2 is missing>
```

---

<!-- Add your multi-step setup flows below this line. -->