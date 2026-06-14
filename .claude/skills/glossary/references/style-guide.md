# Style Guide Reference

Rules for applying glossary terms in documents.  
Maintained as a reference file — consumed by `SKILL.md`.

---

## 1. Capitalization

- Use **title case** for proper nouns, named document types, and UI element names: *Table of Contents*, **Save** button, *Release Notes*.
- Use **sentence case** for general technical writing concepts in body text: *active voice*, *metadata*, *content reuse*.
- When in doubt, follow the capitalization specified in your project's style guide.

---

## 2. Abbreviations and Initialisms

- Spell out any term on its first use, followed by the abbreviation in parentheses: "subject matter expert (SME)."
- Do not introduce an abbreviation if the term appears fewer than three additional times after its first use.
- After first use, the abbreviation alone is sufficient.

---

## 3. Inline Definition vs. Glossary Reference

**Define inline when:**
- The term appears only once or twice in the document.
- The audience is unlikely to consult a glossary.
- The definition is one sentence or fewer and does not disrupt reading flow.

**Refer to the glossary when:**
- The term requires more than one sentence to define.
- The term appears multiple times across the document.
- The term has important usage notes or cross-references.

Use a consistent cross-reference format: "See *[Term]* in the Glossary."

---

## 4. Preferred Terms

- Where the glossary lists synonyms, always use the form listed first unless your house style guide specifies otherwise.
- Flag synonym conflicts (e.g., *callout* vs. *admonition*) in your project's terminology decisions log.

---

## 5. Extending the Glossary

When adding a new entry to `references/glossary.md`, use the Standard Entry Format defined in `SKILL.md`. Every new entry must:

- Provide a precise, non-circular definition.
- Identify the part of speech.
- Include a usage example.
- Note any cross-industry variation if known.
- Be inserted in alphabetical order.
