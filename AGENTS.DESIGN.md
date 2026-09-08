# AGENTS.DESIGN.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Iterative Design Protocol

For ordinary design work:
- Work through material decisions in ongoing user dialogue.
- Keep a concise working record of confirmed decisions, proposals, and open questions.
- Address one decision or tightly related group at a time.
- Before consequential planning or document changes, summarize the current assignment, constraints, and intended change for confirmation.
- Keep specifications and plans current as decisions are accepted.
- Identify when later decisions supersede earlier decisions or document content.
- Defer choices that do not affect current scope or architecture.
- Do not force strategy menus, parallel alternatives, subagents, or extra artifacts.
- Recap the agreed state when the discussion becomes long or fragmented.

---

## Skeleton Spike Protocol

From a given spec doc, generate one targeted skeleton spike when a material structural question remains unresolved. Generate multiple spikes only when the user explicitly requests parallel attempts.

- The manager defines the architectural question and constraints.
- A subagent may implement a bounded spike under `AGENTS.SUBAGENTS.md`.

Definition:
- A skeleton spike is a shallow, boundary-spanning, disposable implementation whose purpose is to force concrete architectural commitments.
- It defines the minimal set of modules, interfaces, and constructor signatures required to implement a spec.

Constraints:
- Each spike must make concrete architectural choices wherever the spec is ambiguous. Parallel spikes must make different choices.
- Spikes must define concrete components that correspond to responsibilities or boundaries implied by the spec.
- Components may declare ownership of responsibilities but must not implement substantive behavior for those responsibilities.
- Role-only abstractions that defer commitment are not allowed.
- Code does not need to run or be complete.
- No TODOs.
- No explanatory comments or design narration.
- No attempt at refactoring, reuse, optimization, or cleanliness.

Output:
- One code artifact per spike.
- No prose, commentary, or comparison.

---

## Axis of Variation Discovery Protocol

Before generating parallel or iterative attempts:
- Discover design axes.
  - Analyze the spec for design decisions that could meaningfully alter implementation.
  - This includes choices of tools and external libraries that the strategy relies on.
  - For every external dependency referenced in the spec, include a provider or implementation-choice axis.
  - Also include different approaches to abstraction and modularity.
  - Do not assume all relevant decisions are explicitly stated.
  - Surface any strategic choices the spec depends on, even if they are not stated.

- For each axis, assign exactly one variation role:

  **Decide Upfront:**
  Choices that should be discussed and decided interactively, rather than independently selected across parallel attempts, because mixing them would make different versions uncomparable.

  **Vary Across Attempts:**
  Choices that can be independently selected in different attempts, where different architectures, tools, and approaches can be evaluated and compared.

  **Deferred:**
  Choices that can be stubbed, simplified, or postponed without constraining later decisions or architectures.

- Use the Decide Upfront role sparingly: Only when the decision would reshape all parallel attempts.
- For each axis, define the available choices, and include a one line rationale explaining why the assigned role is appropriate.
- Present the results in plain markdown, such that they are legible in raw form.
- Please stay concise!

- Use the full `AGENTS.AXES.md` creativity and artifact workflow only when explicitly requested.

---

## Parallel Attempt Generation Protocol

When asked to plan or produce multiple “attempts” or versions:
- Do the Step 1 "Understand the Assignment" check just once. After I confirm, you can proceed with all attempts.

- Treat the attempts as **independent explorations of the same problem**, not sequential refinements or variations derived from one another.
- Each attempt must be **self-contained and internally consistent**.
- Attempts should **not learn from, reference, or build upon** each other’s ideas or artifacts. They are created in parallel, not serially.
- Encourage **creative divergence**. Consider exploring different:
  - Intuitive mental models of the problem domain
  - Primary data abstractions and models
  - Architectures
  - Organizational philosophies
  - Levels of abstraction and modularity
  - Numbers and ordering of implementation stages
- When using subagents, follow `AGENTS.SUBAGENTS.md`.
- The manager prepares the shared assignment and assigns each attempt its variation choices.
- The manager may generate one attempt; subagents generate the others independently.
- Isolate workspaces, branches, or output targets when attempts modify code.
- Choose a cost- and capability-conscious model mix:
  - Use manager-class models when creativity or architectural judgment merits it.
  - Use lower-cost models for constrained or technical attempts.
- Do not generate attempts unlikely to improve the final decision.
- After all attempts are complete, the manager compares them, selects a base, and synthesizes only justified improvements.
- **DO NOT ALLOW** feature-creep or unnecessary complexity. Each attempt should be **simple, elegant, and clearly differentiated** in its **core strategy**, not distinguished by layering on frivolous extras or exceeding scope.
- **DO NOT USE production/ops/instrumentation features** as a way to differentiate attempts!
- **DO NOT USE different types of UI (e.g. CLI, GUI, REST API, etc)** as a way to differentiate attempts!
- If a UI is specified, then **ALL VERSIONS** must implement **THAT SPECIFIC TYPE OF UI**.
- If no UI is specified, then all plans and implementations **MUST BE UI-AGNOSTIC**, exposed only as **importable objects** with method-based access!
- Shared elements are acceptable when they represent **universally sound logic** rather than lazy copying.
- Each attempt should be **simple and elegant**, with at least one **distinct rationale or design emphasis** that sets it apart from the others.
- If you are “tempted” to add any of the forbidden items above, **STOP** and choose another axis of variation instead!

---

## Interactive Strategy Selection Protocol

Use only when the user explicitly asks to explore strategies interactively.

- Propose one brief, distinct strategy at a time.
- I will say things like, "Accept", "Reject", "Clarify", "More like this", etc.
- Continue until I select a direction or say the set is sufficient; do not require a predetermined number of strategies.
- Do not generate full implementation plans automatically.
- Use the planning rules when the user requests a plan for a selected strategy.

---

## Comparison and Evaluation Protocol

Use this protocol only when I ask for a **"full comparison,"** or **"comparison protocol."**
It is not necessary to use this protocol for **"brief comparisons."**

When comparing multiple attempts, versions, or branches:

### Step 1: Score and describe each version individually

For each version, provide **explanations and 1-5 star ⭐ ratings** in these dimensions:
- **Correctness**, properly adhering to the feature specs and constraints.
- **Clarity and organization** of structure or writing.
- **Creativity and ingenuity** of approach (diversity, inspired design, or clever solutions, as appropriate).
- **Architectural elegance** (modularity, separation of concerns, generality).
- **Abstraction and conceptual clarity** (objects and their responsibilities are intuitive, reusable, and well-scoped).
- **Simplicity and focus** (avoidance of premature complexity or feature creep).
- **Overspecification or vagueness**, where applicable (e.g. in implementation plans).
- **Overall quality**.

Rating Guidelines
- Use colored, visual stars like this: ⭐⭐⭐☆☆
- Be harsh! Be critical! Do not be generous! Every plan should not get 4 stars out of 5!
- Verify the rating format before continuing.

### Step 2: Compare across versions

Describe for each version:
- **Pros and cons**, relative to the others.
- **Unique contributions** not found in other versions.
- Any **regressions or losses** compared to a defined base branch (if applicable).

### Step 3: Recommend a path forward

- Choose **one version to move forward with**, explaining why.
- Suggest any **specific improvements or elements** to pull in from other versions.

---

## Additional Notes

- Assume **git remotes are already configured**. Branches can be checked out directly. If checkout fails, report it.
