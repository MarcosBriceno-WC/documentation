# Style guide

> **How to use this file:** This is the single source of truth for writing standards across all documentation pages. It is shared between the Writer and Reviewer skills. Before using this skill on a new project:
> 1. Fill in all `[bracketed placeholders]`.
> 2. Review the "Project-specific overrides" section at the bottom and complete it.
> 3. Where two options are offered, pick one and delete the other.
>
> If a rule needs to change mid-project, update it here and note the change date. Do not create separate override files.

---

## Introduction

The goal of this guide is to ensure all `[Project name]` documentation is clear, accurate, and helpful. The content transforms complex technical information into guides that empower `[describe the target audience, e.g. DevOps Engineers, Software Developers, IT/Automation teams]` to use the platform.

---

## Core principles

- **Clarity**: Use plain language and avoid jargon.
- **Accuracy**: All content must come from the provided source materials (transcripts, product documents, etc.). Do not invent features or make assumptions.
- **Consistency**: Use the same terms, formatting, and voice across all guides to build user trust.
- **Empowering tone**: Adopt a calm, approachable, and empowering guide voice.

---

## Voice and tone

- **Professional but casual**: The tone is professional but not stiff or overly formal. Avoid slang.
- **Clear**: Use plain language and short, direct sentences. Avoid complicated vocabulary. Aim for sentences of 20 words or fewer whenever possible.
- **Empowering**: Avoid demanding phrases.
  - Don't use: "You need to select a Workspace first."
  - Use: "To begin, select a Workspace." or "The next step is to select a Workspace."
- **Supportive**: Acknowledge when a topic is complex and provide clear solutions.
- **Human (for introductions)**: For introductory and concept pages, use a more friendly and human tone to connect with the user's needs.
- **Inclusive**: Use gender-neutral pronouns (`they`, `their`). Avoid idioms and culture-specific metaphors that may not translate well.

---

## Formatting and structure

### Headings

- Do not use bold for headings.
- Use sentence case (only capitalise the first word and proper nouns).
- Use imperative verbs where possible — they are scannable and action-oriented.
  - Correct: `## Create a webhook`
  - Incorrect: `## How to Create a Webhook`
  - Incorrect: `## **Create a webhook**`

### Page titles

- Use active, not passive, titles.
  - Don't use: "When a workflow gets stuck"
  - Use: "Handle stuck workflows"
- Keep titles to 60 characters or fewer.

### Introductions

- Start every page with a short, un-bolded introduction that summarises the page's purpose.
- Do not bold any words in introduction sections.
- Do not teach theory in introductions — save that for concept pages.

### User interface elements

- Use bold for user interface elements, buttons, and navigation paths only.
- Example: Click the **Save** button to keep your changes.
- Example: Navigate to **Settings > Integrations**.

### In-page navigation

For long articles with a main H2 heading followed by many H3 subheadings, add a bulleted list of the H3 titles under the H2. This acts as an in-page table of contents. Only include this when there are more than four H3 subheadings.

### Tables

- Use tables instead of bulleted lists for comparison-type content.
- Always include a header row followed by a separator row (`|---|`).

### Images and diagrams

- Format: SVG or PNG with transparent background.
- All images must have descriptive alt text of 120 characters or fewer. Describe the intent, not the appearance.
- Prefer Mermaid diagrams for flows and architecture — they are diff-able and maintainable in a repository.

### Quotation marks

- Use quotation marks only for exact values the user must type or enter word for word.
- Do not use quotation marks for UI labels or buttons — those are **bold**.
- Example: In the **Name** field, enter "revenue this month".
- Example: Set the condition to "status == complete".

---

## How-to step formatting

> **Project decision:** Choose one option below and delete the other before using this skill.

### Option A — Narrative steps (H3 headings)

Best for: complex processes where context and explanation matter as much as the action itself.

- Do not use numbered lists for procedures.
- Each major part of the process is a step, formatted as an H3 heading: `### Step 1: [Descriptive title]`
- Follow each step heading with paragraphs that explain the process in detail.
- You may use a bulleted list within a step for short, individual actions (e.g. clicking a button, entering a value).

### Option B — Numbered list steps

Best for: quick, action-focused procedures where the action is more important than the explanation.

- Use numbered lists for all procedures.
- Begin each step with a bold imperative verb: `1. **Create** your template`
- Add optional sub-steps, code snippets, or expected results indented below the step.
- Include at least one sentence of context before presenting a list of steps whenever possible.

---

## Code and samples

- Always include the language tag immediately after the opening code fence.
- Add a filename or title label when the file name is relevant to the user.
- Highlight specific lines when drawing attention to a change or key detail.

Example:

````md
```bash title="install.sh"
curl -sSfL https://cli.example.com | sh
```
````

---

## Links and callouts

- Use descriptive markdown links — avoid bare URLs in body text.
- Use callouts for extra tips, caveats, or links to related conceptual guides.

Available callout types:

| Type | When to use |
|---|---|
| `note` | Additional context that is helpful but not critical |
| `tip` | Optional shortcuts or best practices |
| `info` | Neutral, supplementary information |
| `warning` | Actions that may cause data loss or unexpected results |
| `danger` | Irreversible actions or serious consequences |

> Check `ProjectConvention.md` for the exact callout syntax used by this project's platform.

---

## Grammar and punctuation

- Do not use em dashes (—). Use commas, parentheses, or colons to set off phrases instead.
- Use digits for numbers in technical contexts ("3 retries", "5 minutes").
- Use serial (Oxford) commas.
- Meticulous attention to grammar, spelling, and punctuation is required at all times.

---

## Plain language

Replace complex words with simpler alternatives:

| Use | Instead of |
|---|---|
| use | utilize / leverage |
| get | obtain |
| before | prior to |
| because | due to the fact that |
| if | in the event that |
| help | facilitate |

---

## Words and phrases to avoid

Avoid the following in all documentation:

- `important`
- `very`
- `easily` / `easy`
- `quick` / `quickly`
- `simply` / `just` / `obviously`
- `with confidence`
- `things` (as in "handle things") — be specific instead
- `leverage` — use "use" or "using"

**AI-generated words to avoid:**
- `delve`
- `seamless` / `seamlessly`
- `robust`
- `building blocks`
- `unlock`
- `cutting-edge`
- `revolutionize`

---

## SEO and metadata

| Field | Rule |
|---|---|
| `title` | 60 characters or fewer. Start with the task or concept. Avoid duplicating titles across the same section. |
| `description` | One concise sentence, 120–155 characters. Begin with an action verb: "Learn how to…" or "Reference for…". |
| `keywords` | 3–6 singular nouns or phrases. Lowercase. Reuse terms already present in the page headings. |
| `slug` | Lowercase, hyphenated, no special characters. |

---

## Missing information

If information is missing from the source material and clarification is needed, add a note explicitly in the draft.

Format: `[Note: Need clarification on [specific topic or parameter].]`

---

## "Related articles" section

When a guide needs a "Related articles" section, use this format exactly. The number of cards and column count may vary — adjust `cols` to match the number of cards (maximum 3 columns).

```mdx
## Related articles

Now that you know how to [complete the main task of this guide], you can explore these related guides.

<CardList cols={3}>

  <Card title="[Guide title]" icon="[icon-name]" link="/[path/to/guide]">
    [One sentence describing what the user will learn.]
  </Card>

  <Card title="[Guide title]" icon="[icon-name]" link="/[path/to/guide]">
    [One sentence describing what the user will learn.]
  </Card>

  <Card title="[Guide title]" icon="[icon-name]" link="/[path/to/guide]">
    [One sentence describing what the user will learn.]
  </Card>

</CardList>
```

> Check `ProjectConvention.md` for the available icon names for this project.

---

## Project-specific overrides

> Complete this section before using this skill. These rules take priority over the defaults above when there is a conflict.

### Protected terminology

List any terms that must always appear exactly as written — do not paraphrase, shorten, or substitute these.

| Term | Notes |
|---|---|
| `[exact term]` | `[e.g. Always use this exact phrase. Do not substitute.]` |

### Bolding exceptions

List any exceptions to the default bolding rules for this project.

- `[e.g. Do not bold words in introduction sections.]`
- `[e.g. Bold the product name on first mention per page.]`

### Tone adjustments

- `[e.g. This client prefers a more formal tone. Avoid contractions.]`
- `[e.g. Use "you can" instead of "you must" throughout.]`

### Words and phrases to avoid (project-specific)

- `[word or phrase]` — `[reason or alternative]`

### Heading convention

- `[e.g. This project uses title case for all H2 headings.]`
- `[e.g. Step headings must follow the format "Step N: Title".]`

### Additional rules

- `[Any other client-specific rules that do not fit the categories above.]`
