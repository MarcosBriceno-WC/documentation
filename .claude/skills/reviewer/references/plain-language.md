# Plain language checklist

Apply this to every review, regardless of Diataxis category.

---

## Sentences

| Check | Good | Bad |
|---|---|---|
| Active voice | "Click Save" | "The Save button should be clicked" |
| One idea per sentence | — | Two clauses joined with "and" when they should be separate |
| 15–20 word average | — | Sentences over 30 words |
| Front-loaded | "Use `--verbose` to see detailed output" | "Detailed output can be seen by using `--verbose`" |
| Direct address | "You can configure..." | "Users can configure..." |

---

## Words

### Cut these words and phrases

| Instead of | Use |
|---|---|
| utilize | use |
| in order to | to |
| it is important to note that | (delete — then make the point) |
| leverage | use, apply, take advantage of |
| perform configuration of | configure |
| in the event that | if |
| it is recommended that | recommend (then state the recommendation) |
| please note that | (delete) |
| simply / just | (delete — it implies the task is easy, which may not be true for the reader) |
| obviously / clearly / of course | (delete — condescending if the reader doesn't find it obvious) |

### AI-flavoured and filler language

Flag any of the following as **Minor**. These words signal vague, inflated, or AI-generated writing — they add length without adding meaning. Cut them or rewrite the sentence to say something specific.

**Hollow metaphors** — these are imprecise and carry no real information:

| Flag | Why |
|---|---|
| building blocks | what are they, specifically? |
| cornerstone | vague importance claim |
| backbone | same |
| ecosystem | almost always replaceable with the actual thing |
| landscape | "the payments landscape" means nothing |
| journey | users don't go on journeys; they complete tasks |
| empower / enable | say what the feature actually does |
| unlock | say what becomes possible, specifically |
| seamless | every product claims this; it means nothing |
| powerful | show don't tell — describe the capability |
| robust | same |
| cutting-edge / state-of-the-art | same |
| world-class | same |
| next-level | same |

**Filler openers** — sentences that delay the point:

| Flag | Fix |
|---|---|
| "It's worth noting that..." | delete, then make the point |
| "It's important to understand that..." | delete, then make the point |
| "One of the key things to keep in mind..." | delete, then make the point |
| "At the end of the day..." | delete |
| "In today's world..." | delete |
| "When it comes to X..." | start with X |
| "This section will cover..." | just cover it |
| "In this guide, we will explore..." | just do it |

**Vague intensifiers** — words that claim significance without providing it:

- various, numerous, multiple (be specific: how many? which ones?)
- significant, substantial, considerable (quantify it)
- straightforward, easy, simple (delete — the reader decides)
- comprehensive, complete, full (usually untrue, always unverifiable)
- advanced, sophisticated (say what it actually does)

**Hedge stacking** — one hedge is sometimes appropriate; two or more in a row is not:

> "This may potentially cause some issues in certain scenarios."

Flag any sentence with more than one hedge word (may, might, could, potentially, sometimes, in some cases, generally, typically, usually). Rewrite to be precise about when and under what conditions.

### Em dashes

Do not use em dashes (—) anywhere in the docs. Flag every instance as **Minor** and suggest a rewrite.

Em dashes are almost always a sign that a sentence is doing too much. Rewrite by splitting the sentence or choosing a more precise construction:

| Instead of | Use |
|---|---|
| "The endpoint returns a token — you'll need this for subsequent requests." | "The endpoint returns a token. Use it for subsequent requests." |
| "Configure the timeout — the default is 30 seconds — before deploying." | "Configure the timeout before deploying. The default is 30 seconds." |
| "There are three methods — GET, POST, and DELETE — supported by this API." | "This API supports three methods: GET, POST, and DELETE." |

If the em dash is separating a parenthetical, use a comma or rewrite. If it's introducing a list or explanation, use a colon.

### Terminology consistency

- Pick one term per concept. Do not alternate between "workspace" and "project" if they mean the same thing.
- Use the same term the UI uses. If the button says "Save", the docs say "Save", not "store" or "commit".
- Define terms on first use if there's any ambiguity. Don't define them again.

---

## Headings

### Style by doc type

| Doc type | Heading style | Example |
|---|---|---|
| How-to | Verb phrase | "Configure authentication" |
| Tutorial | Task phrase | "Create your first project" |
| Reference | Noun phrase | "Configuration options" |
| Explanation | Question or concept | "How caching works" |

Headings should be scannable. A reader skimming headings should be able to understand the doc's structure.

Avoid: "Overview", "Introduction", "Additional information" — these tell the reader nothing about the content.

### Sentence case

All headings and the page title must use sentence case: capitalise only the first word and proper nouns. Title case is not used.

| Correct | Incorrect |
|---|---|
| `## Create your first project` | `## Create Your First Project` |
| `## Configuration options` | `## Configuration Options` |
| `## How authentication works` | `## How Authentication Works` |
| `# Server-to-server payments guide` | `# Server-To-Server Payments Guide` |

Proper nouns (product names, brand names, acronyms) are always capitalised regardless of position: "Set up OAuth 2.0", "Configure Stripe webhooks".

Flag every violation as **Minor**, but list them all — casing errors are easy to fix and should be resolved in one pass.

---

## Procedures

- Lead every step with a verb: "Click", "Run", "Enter", "Select"
- One action per step — if a step has "and then", split it
- State the result after the action if it's not obvious: "The dashboard opens."
- Use code formatting for all commands, file names, parameter names, and UI labels

---

## Numbers and formatting

- Spell out numbers one through nine; use numerals for 10 and above
- Use numerals for all measurements, versions, and quantities regardless of size: "3 seconds", "v2 release"
- Use contractions — they sound human ("you'll", "it's", "don't")
- Avoid parentheses where possible — if the information matters, put it in the sentence; if it doesn't, cut it

---

## Tone

Technical writers should be:
- **Direct**: Say what you mean. Don't hedge unless there's real uncertainty.
- **Respectful**: Assume competence. Don't over-explain things the reader already knows.
- **Neutral**: Avoid marketing language in docs ("powerful", "seamless", "easy").
- **Specific**: "Run this command to export your data" beats "There are various ways to export."

---

## Acronyms

Introduce every acronym on first use with the full term first, acronym in parentheses immediately after:

> Web Content Accessibility Guidelines (WCAG)

After the first use, the acronym alone is fine. Flag as **Minor** if:
- The acronym appears before it's been introduced ("WCAG is a standard..." with no prior definition)
- The format is reversed: `(WCAG) Web Content Accessibility Guidelines`
- The acronym is introduced more than once in the same document
- The parenthetical uses the wrong case or punctuation: `Web Content Accessibility Guidelines [WCAG]` or `web content accessibility guidelines (wcag)`

Use judgement for ubiquitous acronyms (API, URL, HTML, JSON) — flag only if the doc's audience might genuinely not know them.

---

## Lead-in sentences

Every block element must be introduced by a sentence before it appears. This applies without exception to:

- Lists (bulleted and numbered)
- Tables
- Code blocks
- Images and diagrams
- Notes, warnings, and callout boxes

The lead-in sentence should tell the reader what the element contains or why it's there — not just "The following table shows..." as empty throat-clearing, but a sentence that adds real context.

| Good | Bad |
|---|---|
| "The following parameters control retry behaviour:" | *(list with no introduction)* |
| "The table below compares authentication methods by security level and setup complexity:" | "The following table:" |
| "Use this command to initialise the project:" | *(code block dropped in mid-paragraph)* |

Flag as **Minor** for each missing lead-in. If a section has multiple bare blocks in a row, flag once and note the pattern rather than listing every instance.