---
name: glossary
description: Use this skill to ensure consistent terminology and precise definitions in technical writing projects. Consult before drafting, during editing, or when adding new glossary entries.
---

# Technical Writer's Glossary — Skill

**Version:** 1.0  
**Purpose:** Enforce consistent terminology across all documentation.

---

## When to Use This Skill

| Situation | Action |
|---|---|
| Starting a new document | Consult the glossary before drafting |
| Unsure of a term's preferred form | Look up the entry; use the form listed first |
| Need to define a term inline | Check the style guide rule on inline vs. glossary reference |
| Adding a new term | Follow the Standard Entry Format and insert alphabetically |

---

## Standard Entry Format

```
### Term [Part of Speech]
**Definition:** Precise, non-circular explanation.
**Usage Context:** Where and when this term applies.
**Example:** A sentence demonstrating correct use.
**Related Terms:** Synonyms, antonyms, or associated terms.
**Usage Note:** Common errors or misapplications. (Optional)
⚠️ Variation Note: Differences across style guides or industries. (Optional)
```

---

## Key Rules (Quick Reference)

- Terms marked **[Preferred]** take precedence over listed synonyms.
- Spell out any abbreviated term on first use, followed by the abbreviation in parentheses.
- Do not introduce an abbreviation used fewer than three additional times.
- When a term needs more than one sentence to define, use a glossary reference — not an inline definition.
- Flag cross-guide conflicts using the `⚠️ Variation Note` field.

---

## Reference Files

All glossary entries and style rules are maintained in the `references/` folder:

- **[`references/glossary.md`](references/glossary.md)** — Full alphabetical glossary with all entries.
- **[`references/style-guide.md`](references/style-guide.md)** — Capitalization, abbreviation, inline definition, and extension rules.
