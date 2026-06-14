# Known Discrepancies

> **How to use this file:** Document gaps between what the OpenAPI spec
> says and what the live API actually does. This file has two sections:
>
> - **Pre-known:** Seeded by the author before testing begins, from client
>   briefings, changelogs, or prior knowledge.
> - **Discovered:** Appended by the skill during testing whenever a
>   real-world behavior differs from the spec.
>
> After the author validates a Discovered entry, it can be moved to
> Pre-known and the OpenAPI spec should be updated to match.

---

## Pre-known Discrepancies

| Endpoint | Type | Spec says | Live API does | Spec updated? |
|---|---|---|---|---|
| | | | | |

**Types:** `field-name` · `field-missing` · `field-extra` · `response-schema` · `status-code` · `behavior`

---

## Discovered Discrepancies

> The skill appends entries here during testing. Each entry includes the
> date it was found and the raw evidence (error message or response body).

---

### Template

```
### <YYYY-MM-DD> — <Endpoint Method + Path>

**Type:** <field-name | field-missing | field-extra | response-schema | status-code | behavior>
**Spec says:** <what the OpenAPI spec documents>
**Live API does:** <what actually happened>
**Evidence:**
<paste the relevant error message, response body snippet, or HTTP status>

**Action taken:**
- [ ] Bruno file updated
- [ ] OpenAPI spec updated
- [ ] Moved to Pre-known (after author validation)
```

---

<!-- The skill appends new discovered discrepancy entries below this line. -->