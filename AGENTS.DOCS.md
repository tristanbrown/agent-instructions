# AGENTS.DOCS.md
[//]: # (DO NOT EDIT LOCALLY - this file is maintained in the agent-instructions repo and synced.)

---

## Good Practices

### Structure
- Use clean, minimal Markdown.
- Use headings, bullets, and numbered lists, not dense paragraphs.
- Keep each section single-purpose.
- **Bold text:** Useful as in-line headers.

### Conciseness
- Keep it short.
- Delete anything that does not change a decision or action.
- Prefer the shortest wording that stays unambiguous.

## Failure Modes

### Overcomplication
- Turning a short doc into a workflow.
- Adding structure that creates busywork.
- Adding sections that do not change outcomes.
- Rules with caveats and exceptions are **bad rules!**

### Overspecification
- Picking defaults that don't have to be specified.
- Setting arbitrary numerical limits or heuristic rules.
- Introducing arbitrary targets, quotas, or rubrics.
- Using examples that become de facto requirements.
- Making trivial or unimportant decisions upfront. 

### Biasing Examples
- Using examples when the goal is generalization.
- Using sample names or implementation hints that weren’t requested.

### Verbosity
- Long paragraphs for list-like content.
- Bullets that bundle multiple ideas.
- Repeating the same point across sections.

### Poor Formatting
- Deep nesting.
- Overlapping sections.
- Emphasis-heavy formatting that reduces skimmability.
