# AGENTS.ATTEMPTS.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Axis of Variation Discovery Protocol

When we want multiple attempts/plans/versions, use this protocol *before* generating them.

### Goal
Ensure the attempts diverge on the **few high-impact architectural decisions** implied by the spec, while keeping low-impact details stable and avoiding combinatorial explosion.

### Step 1: Identify candidate axes
Generate a short list of candidate axes (typically 6–12). Each axis must:
- Be a real decision that changes **architecture, public API, data contracts, stage ordering, or test fixtures**.
- Have 2–4 plausible options (not something already dictated by the spec).
- Be phrased as a decision question (e.g., "How do we represent X?", not "What should we name X?").

For each axis, list:
- **Axis:** the decision question
- **Options:** 2–4 plausible choices
- **Why it matters:** 1 line describing the structural impact
- **Decide vs defer:** `Must decide for v1` or `Can defer`, with a 1-line reason

### Step 2: Select the variation axes (keep it minimal)
From the candidates, select a minimal set of axes to actively vary across attempts (typically 3–6).
- Prefer axes that are **high uncertainty**, **high leverage**, or **costly to change later**.
- Explicitly mark the rest as **Fixed** (spec-dictated) or **Deferred** (decide later with a trigger).

### Step 3: Create an "Axis Variation Contract"
Before generating attempts, define a contract that maps axes/options onto attempts:
- Each `Must decide for v1` axis should have **at least 2 distinct options represented across attempts** (as the number of attempts allows).
- Avoid varying every axis in every attempt. Prefer:
  - **One primary axis** that differentiates each attempt.
  - At most **one secondary axis** that varies occasionally.
  - Everything else uses a stated default.
- Do **not** attempt full cross-product coverage.

Output format can be a compact table/list, e.g.:
- `Axis -> default -> Attempt A/B/C/D choices`

### Step 4: Make the axes visible inside each attempt
At the top of each attempt/plan, include a brief "Axis Decisions" section:
- For each selected axis: `Chosen: <option>` (or `Deferred: <trigger to decide>`).
- If an axis is deferred, the attempt must still remain **implementable and testable** (e.g., pick one concrete reference backend even if the boundary is generic).

### Guardrails (what is NOT an axis)
Do not treat these as axes unless the spec explicitly makes them central:
- Naming, folder layout, formatting, or minor library choices.
- Production/ops/instrumentation features (auth, hosting, logging, deployment, monitoring, scaling, etc.).
- UI/interface modality changes (CLI vs web vs API), unless explicitly requested.

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
