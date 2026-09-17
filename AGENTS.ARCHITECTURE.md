# AGENTS.ARCHITECTURE.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

These rules define durable responsibility boundaries and sources of truth. Apply them when choosing, planning, or implementing a system structure.

---

## Architectural Rules

1. **Portability through modularity**
   - Structure logic into focused modules, functions, or classes with clear boundaries.
   - Avoid embedding universal logic in places where it cannot be reused.
   - Portable logic should be clean, general, and free of project-specific coupling.
   - Use portability as a test of modularity, not as a reason for speculative generalization.

2. **Separation of concerns**
   - Identify distinct responsibilities and architectural boundaries appropriate to the project.
   - Keep distinct layers of the codebase isolated; for example:
     - UI layout separate from widget logic
     - Widget logic separate from data processing
     - Data processing separate from database access
   - Each layer should be as self-contained and portable as possible.
   - Cross-layer dependencies should be minimal, explicit, and well-defined.
   - Do not introduce layers or abstractions without a distinct responsibility.

3. **Consistency and consolidation**
   - Reuse existing logic and abstractions whenever possible.
   - Consolidate similar solutions when a shared abstraction improves clarity and consistency.
   - Maintain single sources of truth to avoid conflicts.
   - Introducing new patterns is welcome if they clearly improve clarity, adaptability, or replace outdated or messy approaches.

4. **Database schema ownership**
   - When using an ORM or declarative schema tool, define the complete current physical schema in organized table, model, or schema modules using that tool's native abstractions.
   - Treat those current-state definitions as the source of truth and keep database access code aligned with them.
   - Treat migrations as transition history, not as the current schema definition. Each migration should express only the change between two schema states and be as thin as the tool safely permits.
   - Prefer generating migrations from, or validating them against, the declarative schema when the selected tool supports it.
   - Do not reduce an ORM or schema tool to a thin runtime wrapper while placing the real schema definition in migrations.
   - A fresh database must be creatable in the current application-supporting state from the current schema definitions alone, without migration history.
