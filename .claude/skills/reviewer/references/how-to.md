# How-to guide review criteria

## What a how-to guide must do

A how-to guide helps a **competent user accomplish a specific goal**. The reader already knows the basics — they don't need to be taught. They need to get something done efficiently.

## Structure checklist

- [ ] Title is a verb phrase that names the goal ("Configure SSO", "Migrate to v3", "Rotate API keys")
- [ ] Opens with a one-sentence statement of what this guide covers — no background padding
- [ ] Prerequisites are listed explicitly before any steps (software versions, permissions, prior tasks)
- [ ] Steps are numbered and sequential
- [ ] Each step is a single action
- [ ] Ends when the task is complete — no trailing explanation or "further reading" padding

## Content checklist

- [ ] Assumes competence — no explaining what things are unless critical to the task
- [ ] Commands and code are complete and accurate
- [ ] Variations and edge cases are noted inline, briefly ("If you're using X instead of Y, pass the `--flag` argument")
- [ ] Does not include conceptual explanation — that belongs in an Explanation doc
- [ ] Does not teach — that belongs in a Tutorial

## Common how-to guide failures

**Burying the prerequisites**: The reader gets three steps in before discovering they need something they don't have. Prerequisites belong at the top, before step 1.

**Mixed Diataxis**: A how-to that opens with two paragraphs explaining *why* the feature works the way it does. Cut the explanation or move it to a linked Explanation doc.

**Over-specifying**: Telling the reader what to type in a dialog box they've seen a hundred times. Trust the reader's competence.

**Under-specifying**: Skipping steps that seem obvious to the writer but aren't to the reader. If it has to happen, it has to be in the guide.

**Weak title**: "Authentication" is not a how-to title. "Set up OAuth 2.0 authentication" is.