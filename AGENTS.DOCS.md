# AGENTS.DOCS.md
[//]: # (DO NOT EDIT LOCALLY - this file is maintained in the agent-instructions repo and synced.)

---

## Purpose

This doc defines standards for work on documents and the quality of their content.

---

## Good Practices

### Structure
- Preserve existing structure and tone unless asked.
- Use clean, minimal Markdown.
- Use headings, bullets, and numbered lists, not dense paragraphs.
- Keep each section single-purpose.
- Before adding content, assess whether the documentation needs it and which document and section it belongs in.
- Add sections only for distinct topics.
- Use an existing section when it fits.
- **Bold text:** Useful as in-line headers.

### Conciseness
- Keep it short.
- State each concept once, clearly and unambiguously.
- Use direct verbs instead of abstract descriptions of actions.
- Keep a detail only if omitting it would cause misunderstanding or change a decision or action.
- Prefer the shortest wording that stays unambiguous.
- State general concepts directly, not through enumerated cases. Limit enumerations to complete lists of finite sets and necessary illustrations identified as non-exhaustive.

### Correcting documents

A corrected document should present the current understanding, not the history of the edit.

- Replace superseded descriptions with the corrected content.
- Do not preserve superseded descriptions as negations, contrasts, or commentary about the correction.
- Negative constraints must express independent requirements.

---

## Failure Modes

### Overcomplication
- Turning a short doc into a workflow or procedure.
- Adding structure that creates busywork.
- Adding sections that do not change outcomes.
- Reorganizing or replacing content without a clear need.
- Rules with caveats and exceptions are **bad rules!**

### Overspecification
- Picking defaults that don't have to be specified.
- Setting arbitrary numerical limits or heuristic rules.
- Introducing arbitrary targets, quotas, or rubrics.
- Using examples that become de facto requirements.
- Replacing a general concept with a finite enumeration that appears exhaustive (listing A, B, C, D, and E when any letter may apply).
- Making trivial or unimportant decisions upfront. 

### Loss of Intent
- Changing content without understanding its purpose.
- Losing substantive content while condensing or reorganizing.
- Optimizing superficial metrics at the expense of meaning or usefulness.

### Biasing Examples
- Using sample names or implementation hints that weren’t requested.

### Verbosity
- Long paragraphs for list-like content.
- Bullets that bundle multiple ideas.
- Repeating the same point across sections.

### Poor Formatting
- Deep nesting.
- Overlapping sections.
- Emphasis-heavy formatting that reduces skimmability.
- Removing structure that improves readability.
- Content placed under unrelated headings.
- Treating the current document as the default destination for material merely because it arose while that document was being discussed.
