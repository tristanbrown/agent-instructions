# AGENTS.ATTEMPTS.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Parallel Attempt Generation Protocol

- When asked to plan or produce multiple “attempts” or versions, treat them as **independent explorations of the same problem**, not sequential refinements or variations derived from one another.
- Each attempt must be **self-contained and internally consistent**. 
- Attempts should **not learn from, reference, or build upon** each other’s ideas or artifacts. They are created in parallel, not serially.  
- Encourage **creative divergence**. Consider exploring different:
  - Intuitive mental models of the problem domain
  - Architectures
  - Organizational philosophies
  - Data models
  - Levels of abstraction and modularity
  - Engineering strategies
  - Numbers and ordering of implementation stages
- Avoid feature-creep and unnecessary complexity. Each attempt should be **simple, elegant, and clearly differentiated** in its **core strategy**, not distinguished by layering on frivolous extras or exceeding scope.
- Shared elements are acceptable when they represent **universally sound logic** rather than lazy copying.
- Each attempt should be **simple and elegant**, with at least one **distinct rationale or design emphasis** that sets it apart from the others.

---

## Comparison and Evaluation Protocol

When comparing multiple attempts, versions, or branches:
- List **pros and cons** of each relative to the others.
- Note any **regressions or losses** compared to the described base branch, if one is provided.
- Recommend **one version to move forward with**, explaining why.
- Suggest any **specific improvements or elements** to pull in from other versions into the chosen version.

For each version, give explanations and **star ratings (1–5)** along these dimensions:
- **Clarity and organization** of structure and writing.
- **Creativity and diversity** of approaches (e.g. truly distinct ideas vs. reworded variants).
- Highlight any **notable simplifications or elegant solutions**, especially those that reduce premature complexity.
- For outlines or implementation plans, assess **overspecification or vagueness**.
- Overall quality.

Additionally:
- Identify any **unique contributions** that appear in only one version.

Note:
- Assume **git remotes are already configured**. Branches can be checked out directly. If checkout fails, report it.
