# AGENTS.GLOBAL.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

This repository uses layered agent instructions.

`.agents/README.md` is for humans, not agents.

## Routing

Before doing any work, load the instruction files that apply to the task:

1. Read `AGENTS.PROJECT.md` at the project root in full. It contains rules and context unique to the repository and is required for every task.
2. If `AGENTS.LOCAL.md` exists at the project root, read it in full. It contains rules unique to the local workspace.
3. Read each applicable shared rule file from `.agents/`:
   - `AGENTS.CODING.md`: When implementing code or creating implementation plans.
   - `AGENTS.PLANNING.md`: When discussing planning documents, creating implementation plans, or implementing code.
   - `AGENTS.DOCS.md`: When creating or editing Markdown documents.
   - `AGENTS.DESIGN.md`: When making design decisions, exploring alternatives, or generating parallel attempts.
   - `AGENTS.AXES.md`: When explicitly using the full axes-of-variation workflow.
   - `AGENTS.SUBAGENTS.md`: Before any subagent work.

Read every file whose trigger applies. The routed files are cumulative, not alternatives.

## Precedence and conflict resolution

Apply all applicable instructions together. When two instructions cannot both be followed, use this precedence:

1. `AGENTS.LOCAL.md`
2. `AGENTS.PROJECT.md`
3. Applicable shared `.agents/AGENTS.*.md` rule files

Treat an override narrowly:

- An override exists only when applicable instructions directly and irreconcilably conflict.
- Higher-precedence instructions replace only the conflicting requirement. All other lower-precedence instructions remain in force.
- Do not infer an override from silence, omission, greater specificity, later placement, or the task request alone.
- If instructions at the same precedence conflict, or the intended scope of an override is ambiguous, stop before the affected work and ask the user to clarify.
- If an apparent override would relax a prohibition, required approval, safety or privacy boundary, or scope restriction, and that relaxation is not explicit in the higher-precedence instruction, treat the override as ambiguous and ask the user to clarify the intended relationship before proceeding.
- Clarification resolves ambiguity; it does not create an exception that no applicable instruction allows.
