# AGENTS.GLOBAL.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

This repository uses layered agent instructions.

1. **Global rules**
   - `.agents/README.md` is for humans, not agents.
   - The `.agents/AGENTS.*.md` files define universal coding, workflow, and development rules shared across projects.
   - To optimize token usage, some AGENTS files only need to be read in certain scenarios, and can be otherwise skipped. Follow this guide to choosing which AGENTS files to read and obey:
      - `AGENTS.CHAT.md`: Always.
      - `AGENTS.CODING.md`: When we are implementing code or creating implementation plans.
      - `AGENTS.PLANNING.md`: When we are discussing planning docs, creating implementation plans, or implementing code.
      - `AGENTS.ATTEMPTS.md`: When we are discussing, creating, or comparing multiple plan/code versions or parallel attempts.

2. **Project-specific rules**
   - `AGENTS.PROJECT.md` at the project root contains rules unique to this repository.
   - Always read and obey `AGENTS.PROJECT.md`!
   - When global and project rules conflict, the project rules take priority.

---

## Interaction Flow
1. Read all `.agents/AGENTS.*.md` files for global rules.
2. Then read `AGENTS.PROJECT.md` for repo-specific rules.
3. If rules conflict, **project-specific rules override global rules**.  
