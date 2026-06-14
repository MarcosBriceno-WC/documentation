---
name: extract-meeting-knowledge
description: "Use this skill when the user provides a meeting transcript from a client discovery or product explanation session and asks to extract, organize, or process the knowledge from it. Trigger phrases include: 'process this transcript', 'extract knowledge from this meeting', 'organize the client information', 'create meeting notes from this transcript'."
---

# Skill: Extract Meeting Knowledge

## Purpose

This skill processes a meeting transcript from a client discovery or product explanation session. It extracts and organizes the knowledge shared by the client — including concepts, processes, constraints, and documentation directives — into a structured Markdown file ready to be used by writers or AI to produce product documentation.

This skill is **not** a meeting summarizer. It does not capture action items, decisions, or logistics. Its sole focus is the product knowledge the client shared during the meeting.

---

## Trigger

Use this skill when the user provides a meeting transcript and asks to extract or organize the client knowledge from it.

---

## Step 1 — Collect File Metadata

Before reading the transcript, ask the user for the following three values. Ask all at once in a single message:

- **Client name** — the name of the client company or team
- **Product name** — the name of the product or API being documented
- **Meeting date** — in YYYY-MM-DD format

Example prompt to user:
> Before I process the transcript, I need three things to name the output file:
> - Client name
> - Product name
> - Meeting date (YYYY-MM-DD)

Do not proceed until all three values are provided.

---

## Step 2 — Infer Speaker Roles

The transcript will have speaker names but no explicit role labels. Before extracting knowledge, analyze the full transcript to infer which speakers are **client representatives** and which are **facilitators/writers** (your team).

Use the following signals to identify client speakers:
- They explain how the product works, describe features, or define terminology
- They have domain authority — they clarify, correct, or confirm product details
- They say things like "our system", "we built", "the way it works is", "users need to"
- They are the ones being asked questions, not the ones driving the agenda

Use the following signals to identify facilitator/writer speakers:
- They ask clarifying questions
- They summarize back to confirm understanding
- They drive the meeting agenda or take notes out loud
- They say things like "so if I understand correctly", "can you walk us through", "for the docs"

List each speaker and their inferred role in the **Speaker Index** section of the output. This makes the inference auditable.

**Important:** Only extract knowledge from client speakers. Questions or restatements from facilitators should not be treated as product knowledge — unless the client confirms or expands on them.

---

## Step 3 — Extract and Classify Knowledge

Read through the transcript and extract all relevant product knowledge shared by client speakers. Classify each piece into one of the following categories:

### A. Global Documentation Directives
Information that affects the documentation as a whole — not just a single page or feature. Examples:
- Terminology rules ("always call them merchants, not users")
- Tone or audience guidance ("this API is for developers, not end users")
- Structural guidance ("authentication must be explained before anything else")
- Naming conventions for the product, features, or components
- Anything the client says should be consistent across all documentation

### B. Concepts & Definitions
Product-specific concepts, entities, or mental models the client explains. Include:
- What the concept is and what it does
- How it relates to other concepts
- Any nuance in how the client defines it vs. how it might be commonly understood

### C. Processes & Workflows
Any step-by-step flow, sequence, or operational process the client describes. Include:
- The trigger or starting condition
- Each step in order
- The outcome or end state
- Any branching paths or conditional steps mentioned

### D. Constraints, Limitations & Edge Cases
Any boundaries or special conditions that affect how the product behaves. Include:
- Technical limits (rate limits, timeouts, size caps)
- Authentication or permission requirements
- Behaviors that only apply under specific conditions
- Known edge cases or exceptions to general rules

### E. Documentation Emphasis Flags
Things the client explicitly says should be highlighted, warned about, or presented in a specific order in the documentation. Examples:
- "Make sure users understand X before they try Y"
- "This is the part people always get wrong"
- "We need a warning here"
- Prerequisites the client mentions users must meet before a step

### F. Open Questions
Information that was unclear, contradictory, or explicitly left unresolved during the meeting. Include:
- Anything the client said they would follow up on
- Conflicting statements that need clarification
- Topics that were touched on but not fully explained

---

## Step 4 — Evaluate Relevance

Before including any piece of information, apply this filter:

> "Does this information affect how a user of the product understands or uses it?"

- If **yes** → include it
- If **no** (e.g., it's about the client's internal team process, a business decision that doesn't affect the user, or a logistics comment) → exclude it

For **reasons and decisions** (e.g., "we chose webhooks over polling"): only include the reason if it helps the user understand a constraint, behavior, or best practice. Exclude it if it's purely internal context.

---

## Step 5 — Write the Output File

Produce a single Markdown file using the structure below. Save it to:

```
meeting-notes/[client]-[product]-[YYYY-MM-DD].md
```

Use the exact structure defined in the **Output Template** section below. Do not skip sections — if a section has no content, write `_Nothing identified in this meeting._` so the reader knows it was considered.

---

## Output Template

```markdown
# Meeting Knowledge Extract
**Client:** [client name]
**Product:** [product name]
**Meeting Date:** [YYYY-MM-DD]
**Processed:** [today's date]

---

## Meeting Overview

[2–4 sentence summary of what the meeting covered from a product knowledge perspective. What areas of the product were explained? What was the general depth of the conversation? Do not include logistics, action items, or attendee commentary.]

---

## Speaker Index

| Speaker | Inferred Role | Basis for Inference |
|---|---|---|
| [Name] | Client / Facilitator | [brief reason, e.g., "explained product flows, corrected terminology"] |

---

## Global Documentation Directives

> These items affect the documentation as a whole. They should be applied consistently across all pages and content for this product.

### Terminology
[List any naming rules, preferred terms, or terms to avoid. Use a definition list or bullet format.]

### Audience & Tone
[Any guidance on who the documentation is for and how it should be written.]

### Structure & Sequencing
[Any guidance on how content should be ordered, what must come before what, or how the documentation should be organized.]

### Other Directives
[Any other cross-cutting guidance that doesn't fit the above.]

---

## Concepts & Definitions

[One subsection per concept. Use ### for each concept name.]

### [Concept Name]
**What it is:** [Clear explanation based on what the client said]
**Role in the product:** [How it fits into the larger system]
**Related concepts:** [Other concepts from this document it connects to]
**Notes:** [Any nuance, caveat, or distinction the client made]

---

## Processes & Workflows

[One subsection per process. Use ### for each process name.]

### [Process Name]
**Trigger / Starting condition:** [What initiates this process]
**Steps:**
1. [Step one]
2. [Step two]
3. [...]

**Outcome:** [What happens when the process completes successfully]
**Variations / Branching:** [Any conditional paths mentioned]
**Notes:** [Any additional context from the client]

---

## Constraints, Limitations & Edge Cases

[One subsection per constraint or grouped theme. Use ### for grouping if needed.]

### [Constraint or Feature Area]
- [Constraint or edge case, stated clearly and precisely]
- [Another constraint]

---

## Documentation Emphasis Flags

> These are explicit signals from the client about what needs special attention in the documentation — warnings, prerequisites, common mistakes, or sequencing requirements.

- **[Topic]:** [What the client said needs emphasis and why]
- **[Topic]:** [...]

---

## Open Questions

> These items require follow-up before the relevant documentation section can be written.

- **[Topic]:** [What is unclear or unresolved, and what information is needed]
- **[Topic]:** [...]
```

---

## Behavior Notes

- **Preserve the client's language** where possible. If a client uses a specific term to describe something, use that term in the output rather than paraphrasing with a generic word. The terminology section will capture the official terms, but the rest of the document should reflect how the client naturally described things.
- **Do not invent or infer product behavior** beyond what was explicitly stated. If something is implied but not confirmed, put it in Open Questions.
- **Avoid filler.** Every bullet, sentence, and section should carry information a writer needs. Do not pad with phrases like "the client mentioned" or "it was noted that."
- **Concepts and Processes are different things.** A concept is a *thing* (an entity, a model, a construct). A process is a *sequence of steps*. If the client describes both what something is and how it works, split them — define the concept, then describe the process separately.
- **If the transcript is long**, process it fully before writing output. Do not stop mid-transcript.