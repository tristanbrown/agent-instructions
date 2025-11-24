# AGENTS.PLANNING.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Guide for working with planning documents

Planning documents are stored in `docs/`.

Docs named like `*_outline.md` or `outlines/*` define the project's scope.
- Do not modify these unless specifically asked to

Docs named like `*_story.md` or `stories/*` are user stories.
- Each story describes a specific task or goal a user might want to accomplish
- Do not modify these unless specifically asked to

Docs named like `*_plan.md` or `plans/*` are stepwise implementation plans,  
- Generated in response to specific user stories, using outlines for guidance
- Broken down into sequential stages

When asked to generate an implementation plan:  
- ONLY generate a `*_plan.md` or `plans/*.md` file  
- DO NOT begin actual implementation until specifically asked

---

## Rules for splitting implementation into stages

The term **"stage"** refers specifically to implementation steps in a plan document. It does **not** refer to runtime or orchestration pipeline stages. Do not conflate the two.

Refer to templates/plan.V1.md for format.

Composition of stages.
- For each stage, define:
  - The Goal
  - The Scope
  - The Implementation Decisions that have been made
  - The Acceptance Criteria that I, the human developer, need to manually test and evaluate.
- Each stage must add something complete, avoiding **dangling logic or UI**
- The package must be **operable and testable** after each stage
- Prefer making individual stages **self-contained and modular**

Consider the ordering of stages.
- Prefer implementing **isolated or foundational features first**
- Implement **highly intertwined features with many dependencies last**
- Build **core or representative features first**, and add complexity incrementally
- Ensure data input pathways are implemented BEFORE or TOGETHER WITH any feature that needs to use that data!

EXTREMELY STRICT RULE against premature productionization.
- **DO NOT** include production/ops features (auth, hosting, logging, deployment, compliance, job queues, multi-tenant environments, monitoring, hardware scaling, etc.), unless **explicitly** requested.
- Assume **single-user, local-only prototypes**. DO NOT even ATTEMPT to scale this into a production environment, unless **explicitly** requested.
- Build core functionality first. **DO NOT** add unnecessary infrastructure!
- **DO NOT INVENT A UI, CLI TOOL, OR OTHER INTERFACE METHOD** UNLESS EXPLICITLY REQUESTED!
- Assume all plans and implementations **MUST BE** UI-agnostic, exposed only as importable objects with method-based access, unless a **specific UI** is requested.

Every implementation plan must be grounded in concrete decisions.
- When you introduce a concept briefly specify (at a high level):
  - The tech stack it will use
  - The structure or role of the component
  - How it will be used or tested
- An implementation stage that makes no concrete decisions is not an implementation stage.

Level of detail for plans.
- Plans should describe stages, responsibilities, and key constraints, not every detail of implementation.
- Acceptance Criteria should describe observable behavior and operability, not read like unit test code.
- Keep plans concise: prefer short, direct bullets over long paragraphs, and include only details that materially affect architecture, sequencing, or interfaces.

Do quality control to verify these constraints have been followed.
- At the top of the document, please include a brief "Strategy" statement justifying the order of the stages
- Then reevaluate whether the implementation strategy follows the rules here, and refine or reorder stages as necessary

---

## Special rules for database schema and migrations

- Do not create a database before it is necessary.
- **Only add schema when a feature requires persistent data.**
- Let real sample payloads inform table and column design.

- **When schema is needed, implement it in a single, focused stage:**
  - Include table definitions, migration logic, build output, and a smoke test.
  - Do **not** mix schema changes with logic or UI features.
  - Complete the schema stage **before** writing any code that depends on it.

- Once a migration is applied, it **becomes the unified representation of the database** for all future work.
- Avoid scattering follow-up schema tweaks across many later stages.

---

## When asked to begin implementation

- ONLY work on the **specific stage(s)** requested  
- DO NOT get ahead of yourself or implement more than is requested  
- Use the full `outline` and `plan` documents as **context** and **foresight** to guide implementation of each stage
