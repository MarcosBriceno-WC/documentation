# Google Technical Writing style reference

Based on the Google Technical Writing course (https://developers.google.com/tech-writing).

Use this file during Stage 2 to flag violations. All issues are Minor unless marked otherwise.

---

## Words

### Define new or unfamiliar terms
- Introduce any term the reader might not know, either inline or in a glossary.
- Don't define the same term twice.
- For acronyms: see the full rules in `references/plain-language.md` (Acronyms).

### Use terms consistently
- Pick one word per concept. Don't alternate between synonyms (e.g., "send" and "transmit" for the same action).
- Never change a term mid-document for stylistic variety — this is prose writing instinct; fight it in technical docs.

### Use unambiguous pronouns
- Don't use "it", "they", "this", or "that" if the referent is unclear.
- If in doubt, repeat the noun.

> **Bad:** "If the process fails, restart it." (What is "it"?)
> **Good:** "If the process fails, restart the server."

### Prefer active voice
- Subject performs the action: "The function returns a value" not "A value is returned by the function."
- Passive voice is acceptable when the actor is unknown or irrelevant, but flag heavy passive use as Major.

### Use strong, precise verbs
- Avoid weak verb + noun constructions:

| Weak | Strong |
|---|---|
| perform an analysis of | analyse |
| make a decision | decide |
| provide a description of | describe |
| give an indication of | indicate |

- Avoid: "there is", "there are", "it is" as sentence openers — these bury the real subject.

### Cut unnecessary words

| Cut | Replace with |
|---|---|
| at this point in time | now |
| in spite of the fact that | although |
| due to the fact that | because |
| a majority of | most |
| a number of | some / several / many (be specific if possible) |
| the question as to whether | whether |

---

## Sentences

### Focus each sentence on one idea
- If a sentence contains two ideas joined by "and", consider splitting it.
- Long sentences are not automatically wrong, but each clause should earn its place.

### Convert some long sentences to lists
- If a sentence contains three or more items in a series, convert to a bulleted or numbered list.
- "The system supports authentication, authorisation, logging, and rate limiting" → list it.

### Reduce subordinate clauses
- Subordinate clauses beginning with "which", "that", or "who" can often be cut or restructured.
- One or two per paragraph is fine; more is a flag.

### Use parallel construction in lists
- Every item in a list must use the same grammatical form.
- If the first item is a verb phrase, all items must be verb phrases.

> **Bad:**
> - Click the button
> - The form will appear
> - Entering your details
>
> **Good:**
> - Click the button.
> - Enter your details.
> - Submit the form.

---

## Paragraphs

### Open with a topic sentence
- The first sentence of every paragraph should state the paragraph's main point.
- Readers skim — they read first sentences. Don't bury the point.

### One topic per paragraph
- If a paragraph covers two distinct ideas, split it.
- Target 3–5 sentences per paragraph; flag anything over 7.

### Use transitions
- Make the logical connection between paragraphs explicit.
- Don't leave the reader to infer why one paragraph follows another.

---

## Lists

### Use lists appropriately
- Lists work well for: steps, items with no natural prose flow, items that benefit from visual separation.
- Don't convert naturally flowing prose into lists — not everything is a list.

### Bulleted vs numbered
- **Numbered**: use when order matters (steps, ranked items).
- **Bulleted**: use when order doesn't matter.
- Never use a numbered list for unordered items or a bulleted list for steps.

### List item length
- Short items (under one line): no full stop needed.
- Long items (one or more sentences): use full stops consistently across all items.
- Don't mix punctuation styles within a single list.

### Introductory sentence
- Every list must have a lead-in sentence. See full rules in `references/plain-language.md` (Lead-in sentences).

---

## Headers and structure

### Use headers to aid navigation
- Headers should let a reader skim and jump to the section they need.
- Every major topic deserves a header.

### Write descriptive headers
- Headers should tell the reader what the section contains, not label it generically.

| Weak | Strong |
|---|---|
| Overview | What this guide covers |
| Introduction | Why authentication matters |
| Details | Configuration parameters |

- Exception: Diataxis reference docs use noun phrase headers by convention — this is correct.

### Use sentence case
- See full rules and examples in `references/plain-language.md` (Headings → Sentence case).

### Don't skip heading levels
- Don't jump from H2 to H4. Hierarchy must be consistent and logical.