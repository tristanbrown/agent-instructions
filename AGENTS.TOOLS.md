# AGENTS.TOOLS.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

These rules govern how agents execute commands and use tools across repositories.

---

## Git

1. **Authorization**
   - Do not use `git commit` or other repo-altering Git commands, unless I specifically tell you to.
   - If I tell you to work across multiple Git branches, then committing to those branches may be necessary.

2. **Non-interactive operation**
   - Never invoke any interactive Git mode or workflow. This includes, but is not limited to, interactive selection, patch selection, interactive rebasing, and workflows that require responding to prompts or operating an editor, pager, menu, or terminal UI.
   - Do not automate interactive workflows by piping responses, scripting keystrokes, or sending terminal input.
   - Do not bypass this restriction through aliases, wrappers, or scripts.
   - Use non-interactive commands with explicit arguments and inputs.
   - Choose the appropriate procedure for the task while preserving existing work and verifying the result.
