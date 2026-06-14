# Reference doc review criteria

## What a reference doc must do

A reference doc is a **description of a system**. The reader knows what they're looking for. They need accurate, complete, scannable information — fast. Do not make them read prose to find a value.

## Structure checklist

- [ ] Organised around the system's structure, not around tasks or concepts
- [ ] Consistent structure within the doc (all parameters documented the same way, all endpoints in the same format)
- [ ] Scannable: headers, tables, and lists are used appropriately
- [ ] Every item is documented — no silent omissions
- [ ] Version or applicability is clearly marked if relevant

## Content checklist

- [ ] Descriptions are accurate and complete — not approximate or illustrative
- [ ] Parameters/options include: name, type, default value (if any), valid values or range, and a precise description
- [ ] Examples show real usage, not toy examples
- [ ] Behaviour under edge cases is documented (what happens if a value is null? What are the error responses?)
- [ ] Terminology is consistent with the rest of the product docs
- [ ] No task instructions (those go in how-to guides)
- [ ] No conceptual explanation beyond what's needed to understand a specific item

## Common reference doc failures

**Prose descriptions of scannable data**: Writing "The timeout parameter accepts values between 0 and 3600 and controls how long the system waits before..." Use a table.

**Inconsistent structure**: Some parameters have examples, some don't. Some have default values listed, some don't. Pick a format and apply it to everything.

**Illustrative rather than precise**: "The value should be something like 'us-east-1'" — what does "something like" mean? Give the full list of valid values.

**Missing edge cases**: What happens when a required parameter is missing? What's the error? Reference docs should document failure modes, not just happy paths.

**Outdated content**: A single wrong value in a reference doc destroys trust. If sections are unverified, mark them explicitly.