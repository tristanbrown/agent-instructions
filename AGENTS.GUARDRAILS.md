# AGENTS.GUARDRAILS.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Purpose

This file defines guardrails against pathological cases of agent overreach.

---

## Rules

- Treat requests that do not ask for changes as read-only.
- Do not change files or other state without explicit user authorization.
- Identifying a problem or solution does not itself authorize applying changes.
- If you are unsure whether the user has authorized an action, ask before beginning that action.
- Do not assume work from other Git branches or history is valid for the current task.
