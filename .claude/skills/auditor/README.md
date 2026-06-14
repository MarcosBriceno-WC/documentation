# auditor — Claude Skill

A structured content audit skill for technical documentation. Activates Claude as an experienced content auditor — guiding the audit process, evaluating content against defined criteria, and producing deliverables such as inventory spreadsheets, findings reports, disposition matrices, and remediation roadmaps.

---

## File Structure

```
SKILL.md                        # Skill entry point — role definition, phases, and criteria
README.md                       # This file
```

> **Note:** This skill includes glossary entries (Content Audit, Disposition, Remediation, Content Decay, Evergreen Content, and others) intended to be merged into the main `glossary` skill file at `references/glossary.md`.

---

## What This Skill Does

When activated, Claude operates as a structured content auditor. It will:

- Guide you through the five audit phases in order, without skipping steps.
- Evaluate content against seven standard criteria (accuracy, completeness, clarity, style compliance, structural fit, redundancy, and relevance).
- Assign a disposition to each content item (Keep, Minor Update, Major Revision, Restructure, Merge, Archive, Delete, or Needs SME Review).
- Produce structured findings — not rewrites. The auditor assesses; it does not author.
- Flag anything that cannot be assessed without SME input rather than guessing.

---

## How to Use

### 1. Attach to a project

Add this skill to any Claude project where a content audit is planned or in progress. It works alongside the `glossary` skill if both are attached.

### 2. Start with scope definition

Always begin an audit session by defining scope. Use this prompt to kick off Phase 1:

> *"I need to audit [description of content set]. The trigger is [reason]. Help me define the scope and set up the audit framework."*

Claude will walk you through confirming audit boundaries, stakeholders, evaluation criteria, expected deliverables, and timeline before touching any content.

### 3. Work through the phases in order

The skill is structured around five sequential phases. Do not skip ahead — each phase gates the next:

| Phase | What happens |
|---|---|
| **1 — Scope Definition** | Establish boundaries, trigger, stakeholders, criteria, and outputs |
| **2 — Inventory** | Produce a factual catalog of all content items (no evaluation yet) |
| **3 — Evaluation** | Score each item against the seven standard criteria |
| **4 — Disposition** | Assign a recommended action to each item |
| **5 — Reporting** | Produce the audit summary, detailed findings, and optional remediation roadmap |

### 4. Request specific deliverables

Once evaluation is complete, ask Claude to produce any of the standard audit outputs:

> *"Generate an audit summary for stakeholders based on the findings."*  
> *"Format the inventory and dispositions as a structured table."*  
> *"Build a remediation roadmap grouped by effort level."*

---

## Evaluation Criteria

Every content item is scored as **Pass / Fail / Partial / Unable to Assess** across seven criteria:

| Criterion | Key Question |
|---|---|
| Technical Accuracy | Is everything in this document still true? |
| Completeness | Is anything important missing? |
| Clarity | Can the target user understand and act on this? |
| Style Compliance | Does this follow the current style guide? |
| Structural Fit | Is this the right content, in the right place, in the right format? |
| Redundancy | Does this duplicate something else? Which version wins? |
| Relevance | Does this content still serve a current user need? |

If technical accuracy cannot be confirmed without a subject matter expert, Claude will flag the item as **Needs SME Review** and leave that criterion unscored.

---

## Disposition Options

| Disposition | When to use |
|---|---|
| **Keep** | Passes all applicable criteria |
| **Minor Update** | Small corrections needed (broken link, changed UI label, formatting fix) |
| **Major Revision** | Significant accuracy, completeness, or clarity issues |
| **Restructure** | Accurate content, wrong location or format |
| **Merge** | Duplicates another item; consolidate into one authoritative version |
| **Archive** | No longer relevant but has historical or legal value |
| **Delete** | Inaccurate, irrelevant, and no archival value |
| **Needs SME Review** | Technical accuracy cannot be assessed without expert input |

---

## Behavioral Boundaries

This skill has explicit constraints that Claude will enforce throughout the audit:

- **No rewriting during the audit.** Assessment only — content creation happens in a separate phase.
- **No unsupported recommendations.** Every finding must reference a specific criterion.
- **No guessing on technical accuracy.** Uncertain items are escalated, not scored.
- **Findings and recommendations stay separate.** Observations are not decisions.

---

## Merging Glossary Entries

The `SKILL.md` file contains six glossary entries to be added to the main glossary skill:

- Content Audit
- Content Inventory
- Disposition
- Remediation
- Content Decay
- Evergreen Content

Insert these alphabetically into `references/glossary.md` using the standard entry format.
