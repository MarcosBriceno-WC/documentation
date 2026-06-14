# doc-translator-ptbr — Claude Skill

A translation skill for technical documentation from English into Brazilian Portuguese (PT-BR). Produces complete, publication-ready translations of Markdown pages — enforcing consistent terminology, PT-BR register, and structural integrity across multi-file documentation workflows.

---

## File Structure

```
SKILL.md                        # Skill entry point — persona, workflow, terminology, and register rules
README.md                       # This file
```

---

## What This Skill Does

When activated, Claude operates as a senior technical writer and localization specialist. It will:

- Translate technical documentation, API references, developer guides, SDK docs, and fintech content from English into PT-BR.
- Preserve every structural element — headings, anchors, tables, code blocks, links, YAML front matter — without modification.
- Enforce a built-in PT-BR terminology table (overridable by supporting files).
- Apply Brazilian Portuguese grammar, vocabulary, and register conventions throughout.
- Block on ambiguity — if a fintech term is context-dependent or a conflict exists between files, Claude stops and asks before proceeding.
- Leave untranslated anything that must stay in English: code, variables, URLs, product names, HTTP verbs, and specific industry terms (Token, Webhook, Chargeback, etc.).

---

## What This Skill Does NOT Do

- UI string files (`.json`, `.yaml`, i18n files).
- Live website scraping or browser-based translation.
- Non-technical or creative translation tasks.
- Editing, improving, or correcting source content.

---

## How to Use

### 1. Attach to a project

Add this skill to any Claude project where English-to-PT-BR documentation translation is needed.

### 2. Basic translation — single file

Paste or upload a Markdown page and ask for a translation:

> *"Translate this page into PT-BR."*  
> *"Traduz essa página para português."*

Claude will output `<!-- PT-BR -->` as the first line, followed immediately by the translated document — no preamble, no closing note.

### 3. Multi-file workflow — with supporting files

For consistency across a documentation set, provide supporting files alongside the source document. Supported inputs:

| File type | Purpose |
|---|---|
| Glossary or terminology sheet | Overrides the built-in terminology table for project-specific terms |
| Prior translated pages | Establishes translation memory for term consistency across pages |
| Style guide | Applies project-specific register or formatting rules |

Always provide supporting files **before or alongside** the source document. Claude reads them first, extracts all term definitions into its internal translation memory, and applies them throughout the translation.

> *"Aqui está o glossário do projeto e uma página já traduzida. Agora traduz essa nova página."*

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
| First line | Always `<!-- PT-BR -->` |
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

Algumas regras importantes para revisar na saída:

- **Merchant** — traduzido como *lojista* ou *estabelecimento*, escolhido uma vez por página e mantido consistente.
- **Request** — *requisição* em contextos técnicos (HTTP); *solicitação* em contextos voltados ao usuário.
- **Imperatives** — instruções procedurais são traduzidas no imperativo: "Call the endpoint" → "Chame o endpoint."
- **actually / eventually** — falsos cognatos. *Actually* → *na verdade* (nunca *atualmente*); *eventually* → *com o tempo* ou *no final* (verificar contexto antes de usar *eventualmente*).
- **support** *(verb)* — nunca *suportar*. Usar *oferecer suporte a* ou *ser compatível com*.
- **perform** — nunca *performar*. Usar *executar* ou *realizar*.

Para a tabela completa de terminologia e regras de registro, consulte `SKILL.md`.

---

## Using Both Translation Skills

Se o projeto exige traduções para PT-BR **e** ES-ES, ambas as skills podem coexistir no mesmo projeto Claude. Cada skill opera de forma independente com sua própria memória de terminologia. Forneça os arquivos de suporte separadamente para cada skill — glossários e páginas traduzidas não são compartilhados entre elas.

