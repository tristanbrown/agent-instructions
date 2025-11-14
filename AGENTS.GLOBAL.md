# AGENTS.GLOBAL.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

This repository uses layered agent instructions.

1. **Global rules**
   - All `.agents/AGENTS.*.md` files are part of the global instruction set.
   - These define universal coding, workflow, and development rules shared across projects.
   - `.agents/README.md` is for humans, not agents.

2. **Project-specific rules**
   - `AGENTS.PROJECT.md` at the project root contains rules unique to this repository.
   - When global and project rules conflict, the project rules take priority.

---

## Interaction Flow
1. Read all `.agents/AGENTS.*.md` files for global rules.
2. Then read `AGENTS.PROJECT.md` for repo-specific rules.
3. If rules conflict, **project-specific rules override global rules**.  
