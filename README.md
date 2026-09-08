# Agent Instructions – Usage Guide
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

This repo holds reusable, layered instructions for AI agents.
`AGENTS.GLOBAL.md` routes agents to the appropriate topic-specific files.
Projects pull the instruction suite into `.agents/` using **Git subtree (with squash)**.

## Repository Setup

Add the instruction suite to a new project:

    git remote add agent-instructions git@github.com:tristanbrown/agent-instructions.git
    git fetch agent-instructions
    git subtree add --prefix=.agents agent-instructions main --squash

Then copy the inactive starter templates to the project root and customize `AGENTS.PROJECT.md`:

    cp .agents/templates/root-agents.template.md AGENTS.md
    cp .agents/templates/project-agents.template.md AGENTS.PROJECT.md

Do not overwrite existing project instruction files when updating an established project.

Before creating `AGENTS.LOCAL.md`, add this root-anchored rule to the project's root `.gitignore`:

    /AGENTS.LOCAL.md

Verify that the rule applies and that `AGENTS.LOCAL.md` is not already tracked:

    git check-ignore -v --no-index AGENTS.LOCAL.md
    git ls-files -- AGENTS.LOCAL.md

The second command must produce no output.

## Update in an existing project
    git fetch agent-instructions
    git subtree pull --prefix=.agents agent-instructions main --squash

## Notes
- Projects also define `AGENTS.PROJECT.md` for repo-specific rules.  
- The root `AGENTS.md` is only a portable hook to `.agents/AGENTS.GLOBAL.md`.
- `AGENTS.GLOBAL.md` owns routing and precedence. It always routes agents through the project's `AGENTS.PROJECT.md` and optional `AGENTS.LOCAL.md`.
- Files under `.agents/templates/` are inactive templates. Codex does not recognize their template filenames as project instruction files by default.
