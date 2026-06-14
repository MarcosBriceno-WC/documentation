# glossary — Claude Skill

A reusable reference skill for technical writing projects. Ensures consistent terminology, precise definitions, and standardized usage across all documentation.

---

## File Structure

```
SKILL.md                        # Skill entry point — instructions and quick reference
references/
  glossary.md                   # Full alphabetical glossary (30 entries)
  style-guide.md                # Rules for capitalization, abbreviations, and term extension
README.md                       # This file
```

---

## What This Skill Does

When activated, this skill instructs Claude to:

- Use the correct, preferred form of technical writing terms.
- Apply consistent capitalization, abbreviation, and inline definition rules.
- Follow the standard entry format when extending the glossary with new terms.
- Flag terminology conflicts across style guides using `⚠️ Variation Note`.

---

## How to Use

### 1. Attach to a project

Add this skill to any Claude project where technical documentation is being produced. Once attached, it is available throughout the project without any additional setup.

### 2. Consult before drafting

Before writing a new document, ask Claude to confirm the preferred form of any term you plan to use:

> *"According to the glossary skill, what is the preferred term for a background process that runs without user interaction?"*

### 3. Use during editing

Ask Claude to review a draft for terminology consistency:

> *"Review this paragraph for terminology consistency using the glossary skill."*

### 4. Extend the glossary

To add a new term, ask Claude to generate a compliant entry:

> *"Add an entry for 'API reference' to the glossary following the standard entry format."*

Claude will produce a correctly structured entry ready to be inserted alphabetically into `references/glossary.md`.

---

## Reference Files

The skill's logic stays lean by delegating all reference content to two files:

| File | Purpose |
|---|---|
| `references/glossary.md` | Look up definitions, usage context, examples, and related terms |
| `references/style-guide.md` | Look up formatting and usage rules for applying terms in documents |

You can also query these files directly without invoking the full skill.

---

## Adding New Entries

All new entries go into `references/glossary.md`. Every entry must follow the standard format defined in `SKILL.md`:

```
### Term [Part of Speech]
**Definition:** Precise, non-circular explanation.
**Usage Context:** Where and when this term applies.
**Example:** A sentence demonstrating correct use.
**Related Terms:** Synonyms, antonyms, or associated terms.
**Usage Note:** Common errors or misapplications. (Optional)
⚠️ Variation Note: Differences across style guides or industries. (Optional)
```

Insert entries in alphabetical order. Do not add entries directly to `SKILL.md`.

