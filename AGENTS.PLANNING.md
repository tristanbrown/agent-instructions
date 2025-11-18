# AGENTS.PLANNING.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Guide for working with planning documents

Planning documents are stored in `docs/`.

Docs named like `*_outline.md` or in `outlines/` are used to fully specify features.  
- Do not modify these unless specifically asked to.

Docs named like `*_plan.md` or in `plans/` are stepwise implementation plans,  
- Generated from `*_outline.md` or `outlines/*.md` specification files  
- Broken down into sequential stages

When asked to generate an implementation plan:  
- ONLY generate a `*_plan.md` or `plans/*.md` file  
- DO NOT begin actual implementation until specifically asked

---

## Rules for splitting implementation into stages

- For each stage, define the Goal, the Scope, and the Acceptance Criteria that I, the human developer, need to manually test and evaluate.
- The app or project must be **functional and testable** after each stage  
- **“TESTABLE”** means I can try out and evaluate the new feature as an end user, **within the app UI or project API**, not through debug logs or dev tools  
- Prefer implementing **isolated or foundational features first**  
- Implement **highly intertwined features with many dependencies last**  
- Prefer making individual stages **self-contained and modular**  
- Ensure data input pathways are implemented BEFORE or TOGETHER WITH any feature that needs to use that data!

Each stage must:
- Add something **functional and testable**  
- Avoid **dangling logic or UI**

These are **non-negotiable constraints**. Any violation = bad plan.
- At the top of the document, please include a brief "Strategy" statement justifying the order of the stages
- Then reevaluate whether the implementation strategy follows the rules here, and refine or reorder stages as necessary

---

## Special rules for database schema and migrations

- **Database schema changes must be isolated into their own minimal, standalone stage(s)**
- Once a schema or migration is applied, it **becomes the unified representation of the database** for all future work.
- Do **not** mix database changes with other logic or UI feature changes in the same stage.
- A schema-only stage should include:
  - Table changes
  - Migration logic
  - Any build output
  - Smoke test to confirm the app launches and persists data
- Prefer to do schema stages **as early as possible** so that data is created in its proper form, and the same schemas are shared by all downstream stages and branches.

---

## When asked to begin implementation

- ONLY work on the **specific stage(s)** requested  
- DO NOT get ahead of yourself or implement more than is requested  
- Use the full `outline` and `plan` documents as **context** and **foresight** to guide implementation of each stage
