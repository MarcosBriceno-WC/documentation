# doc-translator-eses — Claude Skill

A translation skill for technical documentation from English into Spain Spanish (ES-ES). Produces complete, publication-ready translations of Markdown pages — enforcing consistent terminology, Spain-specific register, and structural integrity across multi-file documentation workflows.

---

## File Structure

```
SKILL.md                        # Skill entry point — persona, workflow, terminology, and register rules
README.md                       # This file
```

---

## What This Skill Does

When activated, Claude operates as a senior technical writer and localization specialist. It will:

- Translate technical documentation, API references, developer guides, SDK docs, and fintech content from English into ES-ES.
- Preserve every structural element — headings, anchors, tables, code blocks, links, YAML front matter — without modification.
- Enforce a built-in ES-ES terminology table (overridable by supporting files).
- Apply Spain Spanish grammar, vocabulary, and register conventions throughout.
- Block on ambiguity — if a fintech term is context-dependent or a conflict exists between files, Claude stops and asks before proceeding.
- Leave untranslated anything that must stay in English: code, variables, URLs, product names, HTTP verbs, and specific industry terms (Token, Webhook, Chargeback, etc.).

---

## What This Skill Does NOT Do

- Latin American Spanish (ES-419) — any dialect, any country.
- UI string files (`.json`, `.yaml`, i18n files).
- Live website scraping or browser-based translation.
- Non-technical or creative translation tasks.
- Editing, improving, or correcting source content.

---

## How to Use

### 1. Attach to a project

Add this skill to any Claude project where English-to-ES-ES documentation translation is needed.

### 2. Basic translation — single file

Paste or upload a Markdown page and ask for a translation:

> *"Translate this page into ES-ES."*  
> *"Traducir esta página al español de España."*

Claude will output `<!-- ES-ES -->` as the first line, followed immediately by the translated document — no preamble, no closing note.

### 3. Multi-file workflow — with supporting files

For consistency across a documentation set, provide supporting files alongside the source document. Supported inputs:

| File type | Purpose |
|---|---|
| Glossary or terminology sheet | Overrides the built-in terminology table for project-specific terms |
| Prior translated pages | Establishes translation memory for term consistency across pages |
| Style guide | Applies project-specific register or formatting rules |

Always provide supporting files **before or alongside** the source document. Claude reads them first, extracts all term definitions into its internal translation memory, and applies them throughout the translation.

> *"Here is our fintech glossary and a previously translated page. Now translate this new page."*

### 4. When Claude stops and asks

If the source document contains an ambiguous fintech term or a conflict between supporting files, Claude will output:

```
CLARIFICATION REQUIRED
```

Followed by a numbered list of specific questions, each quoting the relevant source segment. Answer each question and then ask Claude to proceed. Do not ask Claude to skip or guess — this behavior is intentional.

---

## Output Format

| Rule | Detail |
|---|---|
| First line | Always `<!-- ES-ES -->` |
| Wrapper | No code fence around the document (unless the source itself is fully fenced) |
| Preamble / postamble | None — translation begins immediately after the marker |
| Omissions | None — all source content is translated |
| Additions | None — no translator's notes, commentary, or meta-content |

---

## What Is Never Translated

The following are always preserved verbatim:

- Inline code, fenced code blocks, JSON examples
- Variable names and placeholders (`{merchantId}`, `{{amount}}`, `$TOKEN`)
- URLs and anchor IDs
- Product names and brand names
- API names, endpoint paths, HTTP verbs (GET, POST, PUT…)
- These industry terms: `API`, `SDK`, `Endpoint`, `Token`, `Callback`, `OAuth`, `JWT` (add the words that could not be translated).

---

## Key Terminology Rules

A few rules worth knowing before you review output:

- **biblioteca, not librería** — "library" (software) is always *biblioteca* in ES-ES. *Librería* means bookshop. This is the most common ES-ES localization error in developer docs.
- **la API, el SDK, el JWT** — acronyms take the gender of their underlying noun.
- **actually / eventually** — false cognates. *Actually* → *en realidad*; *eventually* → *finalmente* or *con el tiempo*. Never *actualmente* / *eventualmente*.
- **Merchant** — rendered as either *comercio* or *comerciante*, chosen once per page and held consistently.
- **Request** — *solicitud* in user-facing contexts; *petición* in HTTP/technical contexts.
- **Procedural steps** — default to the infinitive ("Llamar al endpoint"), not the imperative. This is standard in ES-ES technical documentation.

For the full terminology table and register rules, see `SKILL.md`.

