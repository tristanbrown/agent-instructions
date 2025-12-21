# AGENTS.ATTEMPTS.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Axis of Variation Discovery Protocol

Use this protocol when generating multiple plans/attempts, to ensure attempts vary along **high-leverage architectural axes** (not trivia) and avoid converging on the same default decisions.

### Step 0: Understand the assignment (once)
- Reuse the single "Understand the Assignment" pass from the planning workflow.
- Do not start axis discovery until the user confirms the understanding is correct.

### Step 1: Enumerate candidate axes
- List the decisions that most affect:
  - Core abstractions and interfaces
  - Data contracts and persistence shape
  - Feasibility, cost, or performance constraints
  - Irreversibility (expensive to change later)
- Exclude:
  - Any spec-mandated constraints (these must be pinned)
  - Forbidden differentiators (ops/productionization and UI type)
  - Low-impact choices (naming, formatting, minor library preferences)

### Step 2: Propose what to vary vs pin
- Propose a small set of axes to vary across attempts (high impact + plausible alternatives).
- Explicitly list what will be pinned across all attempts:
  - Spec constraints and must/forbidden rules
  - Any assumptions required for comparability
  - Anything the user does not want to spend attention on

### Step 3: Define axis options and decision timing
For each selected axis:
- Provide a short set of mutually exclusive options (phrased at the strategy level).
- Mark the axis as either:
  - **Decide now:** must be fixed to write an executable, stagewise plan.
  - **Defer with a seam:** can be postponed, but each attempt must still choose a concrete **reference path** so stages remain runnable, and must define the minimal contract at the seam.

### Step 4: Build an attempt matrix (strategy cards)
- Create one strategy card per attempt: a 1–2 sentence description that names the chosen option for each varied axis.
- Keep all pinned decisions identical across cards.
- Ensure cards are meaningfully different because of the axes (not extra features).

### Step 5: Axis audit (before writing full plans)
- Verify every selected axis actually varies across attempts (no silent defaults).
- Verify no attempt depends on an unspecified external choice to be actionable.
- If a critical axis is unvaried, either vary it or explicitly justify why it is pinned.

### Step 6: Expand into full plans (Parallel or Interactive)
- **Parallel:** expand each strategy card into a full, self-contained plan.
- **Interactive:** present the strategy cards for accept/reject first; only expand into plans after the set of cards is approved.

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

This is a modified version of the Parallel Attempts Protocol.
- Instead of generating all of the attempts at once, I want you to propose each strategy to me with a BRIEF summary statement. 
- I will say things like, "Accept", "Reject", "Clarify", "More like this", etc.
- We keep going until I have "Accepted" the pre-determined number of different strategies.
- Once you've confirmed I'm happy with our set of strategies, you can generate all of the implementation plans from them, following the rules of the Parallel Attempts Protocol and the planning rules. 

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

### Step 1.5: Did you use the colored stars?
- IF YOU DIDN'T USE THE COLORED STARS, **YOU HAVE TO GO BACK AND REDO STEP 1.** FOLLOW MY INSTRUCTIONS!!!

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
