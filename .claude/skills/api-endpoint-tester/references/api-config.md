# API Configuration

> **How to use this file:** Fill in the values below before starting a
> testing session. The skill reads this file to scaffold the Bruno
> environment and to construct `curl` commands. Update this file if new
> environment variables or auth requirements are discovered during testing.

---

## Environment Name

Used as the `--env` argument when running Bruno.

```
<env-name>
```

Example: `Pay.com Staging`, `Stripe Sandbox`, `Acme API Dev`

---

## Base URL

The root URL for all API requests. Do not include a trailing slash.

```
<base_url>
```

Example: `https://api.staging.pay.com/v1`

---

## Authentication

### Header name

The name of the HTTP header used to pass the API key or token.

```
<auth-header-name>
```

Examples: `x-api-key`, `Authorization`, `x-paycom-api-key`

### Header value format

Describe how the value should be formatted. Include the prefix if required.

```
<auth-header-value-format>
```

Examples:
- `Bearer <token>` — for Bearer token auth
- `<api-key>` — for raw key auth (no prefix)

### API key / token (staging or sandbox)

```
<api-key-or-token>
```

> ⚠️ Never put production credentials here.

---

## Additional Environment Variables

List any other variables that Bruno requests reference with `{{var_name}}`
syntax. Add rows as needed.

| Variable name | Value | Notes |
|---|---|---|
| `base_url` | *(same as Base URL above)* | Always required |
| `api_key` | *(same as API key above)* | Always required |
| | | |

---

## Notes

<!-- Add any environment-specific notes here. For example:
- Rate limits in this environment
- IP allowlisting requirements
- Known instability or maintenance windows
-->