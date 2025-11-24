# AGENTS.ATTEMPTS.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Parallel Attempt Generation
- When asked to plan or produce multiple “attempts” or versions, treat them as **independent explorations of the same problem**, not sequential refinements or variations derived from one another.
- Each attempt must be **self-contained and internally consistent**. 
- Attempts should **not learn from, reference, or build upon** each other’s ideas or artifacts. They are created in parallel, not serially.  
- Some **creative divergence** is encouraged: different structural approaches, organizational philosophies, engineering strategies, data models, levels of abstraction and modularity, numbers of stages, or ordering of stages are all welcome.
- Avoid feature-creep and unnecessary complexity. Each attempt should be **simple, elegant, and clearly differentiated** in its **core strategy**, not distinguished by layering on frivolous extras or exceeding scope.
- Shared elements are acceptable when they represent **universally sound logic** rather than lazy copying.
- Avoid redundancy that produces nearly identical results; ensure each attempt expresses at least one **distinct rationale or design emphasis**.
- Each attempt should be **simple and elegant**, but **distinct in approach** from other attempts.

---

## Comparison Phase Evaluation
- When comparing multiple attempts, versions, or branches, list **pros and cons** of each relative to the others.  
- Note any **regressions or losses** compared to the described base branch, if one is provided.  
- Recommend **one branch to move forward with**, explaining why.  
- Suggest any **specific improvements or elements** to pull in from other versions into the chosen branch.  
- Assume **git remotes are already configured**. Branches can be checked out directly as needed. If checking out a branch fails, please tell me!
