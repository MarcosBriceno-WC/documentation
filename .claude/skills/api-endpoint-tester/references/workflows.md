# Workflows

> **How to use this file:** Document multi-endpoint flows that represent
> real business goals. This file has two sections:
>
> - **Known Workflows:** Seeded by the author before testing, based on
>   client briefings, existing documentation, or prior knowledge. These
>   are treated as the primary testing roadmap.
> - **Discovered Workflows:** Appended by the skill when testing reveals
>   an undocumented sequence or corrects a Known Workflow. The author
>   should validate Discovered entries and promote them to Known once
>   confirmed.
>
> The skill references workflow IDs (e.g. `WF-01`) in Testing-Reports.md
> to keep findings traceable.

---

## Known Workflows

---

### Template

```
### WF-NN: <Workflow Name>

**Goal:** <What business outcome this flow achieves>
**Status:** `untested` | `in-progress` | `verified` | `blocked`

**Sequence:**
1. `POST /<path>` — <what this step does and what it returns>
2. `GET /<path>/{id}` — <what this step does and what it returns>
3. ...

**Prerequisites:** <any resources or state that must exist before step 1>
**Success condition:** <how to confirm the flow completed correctly>
**Notes:** <edge cases, optional steps, or alternative paths>
```

---

<!-- Add Known Workflow entries below this line. -->

---

## Discovered Workflows

> The skill appends entries here when testing reveals a sequence that was
> not documented in Known Workflows. Each entry includes the date it was
> found. Author should validate and move confirmed entries to Known Workflows.

---

### Template

```
### DWF-NN: <Workflow Name> — discovered <YYYY-MM-DD>

**Goal:** <What business outcome this flow achieves>
**Validation status:** `needs-author-review`

**Sequence:**
1. `POST /<path>` — <observed behavior>
2. ...

**How it was found:** <brief description of the testing scenario>
**Open questions:** <anything unclear that the author should confirm>

**Checklist:**
- [ ] Author validated
- [ ] Promoted to Known Workflows as WF-NN
- [ ] workflows.md updated
```

---

<!-- The skill appends Discovered Workflow entries below this line. -->