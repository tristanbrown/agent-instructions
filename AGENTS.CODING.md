# AGENTS.CODING.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

These are universal rules for AI agents across all repositories.  
They define baseline coding style principles that apply everywhere.  

---

## Coding Rules

1. **Implement only what was requested**  
   - Apply YAGNI: do not add unrequested features or speculative flexibility.
   - Apply KISS: use the simplest clear solution that meets current requirements.
   - Do not refactor without explicit instructions to do so.  

2. **Comments**  
   - Purpose: make code human-readable.  
   - Keep them concise and limited to clarifying the broad purpose of code blocks.  
   - Do not use comments as historical logs of edits.  
   - Omit comments when clear naming and structure make them unnecessary.  

3. **Readability through structure**  
   - Avoid excessive nesting.  
   - Use abstraction and modularity to keep top-level code concise and readable, preferably fitting on a single screen.  
   - Favor meaningful names for methods and variables so code is self-explanatory.  

4. **DRY (Don’t Repeat Yourself)**  
   - Consolidate repeated knowledge or behavior when one source improves maintainability.
   - Do not abstract merely similar code without a stable shared concept.

5. **Conciseness**  
   - Prefer simple, direct code that remains readable and easy to debug.
   - Avoid unnecessary boilerplate, wrappers, or abstractions that don’t add clarity.  
   - Do not compress logic when it reduces readability.

6. **Soundness over hacks**  
   - Do not use brittle or hacky workarounds.  
   - Prefer solutions that are maintainable, robust, and aligned with project conventions.  
   - If a proper solution is unclear, ask for clarification instead of guessing.  

7. **Portability through modularity**  
   - Structure logic into focused modules, functions, or classes with clear boundaries.
   - Avoid embedding universal logic in places where it cannot be reused.  
   - Portable logic should be clean, general, and free of project-specific coupling. 
   - Use portability as a test of modularity, not as a reason for speculative generalization. 

8. **Separation of concerns**
   - Identify distinct responsibilities and architectural boundaries appropriate to the project.
   - Keep distinct layers of the codebase isolated; for example:  
     - UI layout separate from widget logic  
     - Widget logic separate from data processing  
     - Data processing separate from database access  
   - Each layer should be as self-contained and portable as possible.  
   - Cross-layer dependencies should be minimal, explicit, and well-defined.
   - Do not introduce layers or abstractions without a distinct responsibility.

9. **Consistency and consolidation**  
   - Reuse existing logic and abstractions whenever possible.
   - Consolidate similar solutions when a shared abstraction improves clarity and consistency.
   - Maintain single sources of truth to avoid conflicts.
   - Introducing new patterns is welcome if they clearly improve clarity, adaptability, or replace outdated/messy approaches.

10. **Thoughtful use of dependencies**  
    - External dependencies are allowed if they are reliable, well-maintained, and reduce workload significantly.
    - Prefer built-in features or existing project utilities when they serve the purpose well, and are maintainable.
    - Avoid reinventing the wheel when a suitable, verified, reliable, well-maintained tool already exists.
    - Avoid unnecessary or redundant dependencies.  
    - If adding a dependency, explain why it’s the right tool.
    - Ensure dependencies are flexible enough to adapt to future needs.

11. **Isolated environments**  
    - Do not install dependencies directly to the host system.  
    - Always use isolated environments (e.g., venv, conda, or language-specific equivalents).  
    - Containerized environments (e.g., Docker) are an exception: system-level installs inside a container are acceptable.  
    - Ensure setups are portable and reproducible across machines.

12. **Testing design**  
    - Focus on realistic behavior, important failure paths, and likely regressions.
    - Match coverage and test level to risk and value; do not require unit, integration, and end-to-end tests for every change.
    - Avoid tests that merely restate hardcoded constraints, schemas, or implementation details.
    - Avoid disposable tests when ad hoc checks suffice.
    - Prefer not to create temporary tests unless needed to guard against a high risk of regression during implementation; remove them before completion.
    - Keep the permanent test suite focused on current expected behavior.
    - Update or remove tests when expected behavior changes.
    - Keep private data out of examples and fixtures.
    - Keep tests performant and concise; reuse setup and fixtures when it improves clarity.

13. **Git restrictions**
   - Do not use `git commit` or other repo-altering git commands, unless I specifically tell you to.
   - If I tell you to work across multiple git branches, then committing to those branches may be necessary. 

---

## Philosophical Note
These rules align with the *Zen of Python* (PEP 20), whose principles are broadly applicable across languages:  
- Readability counts.  
- Simple is better than complex.  
- Flat is better than nested.  
- There should be one obvious way to do it.  

Agents should interpret these rules in the same spirit: clarity, simplicity, and consistency matter most.
