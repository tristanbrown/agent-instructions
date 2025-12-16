# AGENTS.ATTEMPTS.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Axis of Variation Discovery Protocol

Use this protocol when the goal is to generate multiple plans/attempts that are meaningfully different along *important* architectural axes (and not randomly different on low-value details).

### Objective
- Discover the **highest-leverage decision axes** in the spec.
- Explicitly choose which axes should **vary across attempts** and which should be **frozen**.
- Prevent “combinatorial explosion” by making **one coherent choice per attempt** for each varied axis.

### Step 0: Inputs
- The primary spec doc(s) to treat as source-of-truth.
- The number of attempts to generate (e.g. 3–5).
- Any user-stated “must-have” constraints (e.g. UI-agnostic, local-only prototype, etc.).

### Step 1: Extract candidate axes (broad, not detailed)
Propose a short list (typically 5–12) of candidate axes that plausibly change architecture or interfaces, such as:
- External dependency boundaries (e.g. LLM backend/protocol, storage, parsing libraries)
- Core data abstractions (key objects, responsibilities, invariants)
- Pipeline structure (phases, ordering, state transitions)
- Failure/repair policy shape (retry semantics, fallbacks, determinism bounds)
- Test strategy surface (fixtures vs live calls; deterministic vs stochastic layers)

Rules:
- Axes must be **orthogonal-ish** (avoid duplicates).
- Axes must be **decision-shaped** (not “we should be careful”).
- Do **not** include forbidden differentiation items (production/ops, UI type changes), unless explicitly requested by the spec.

### Step 2: Rank axes by leverage (why they matter)
For each candidate axis, provide:
- What breaks/changes if you pick a different option
- The expected impact on complexity and testability
- Whether it creates a “combinatorial explosion” if left open

### Step 3: Freeze vs vary (explicit contract)
Create two lists:
- **Axes to Vary (Must Differ Across Attempts)**: usually 1–3 axes total
- **Axes to Freeze (Must Match Across Attempts)**: everything else that should remain stable

Guidelines:
- Vary only axes that you genuinely want to compare.
- Freeze low-value details so attempts don’t waste divergence budget.
- If an axis is “unknown but explosive” (e.g. “LLM provider choice”), either:
  - make it a *varied axis* (different coherent choices per attempt), or
  - freeze it with an explicit “in-scope now / out-of-scope later” statement.

### Step 4: Attempt briefs (strategy sketch, not full plans)
Before writing full implementation plans, produce a short “Attempt Brief” for each attempt:
- Name + 1-sentence thesis
- The chosen option for each **varied** axis (one option per axis)
- What is explicitly frozen (a short reference to the freeze list)
- 2–4 key consequences (tradeoffs, risks, test approach)

Hard rules:
- Briefs must be **top-down and complete** at the strategy level.
- Briefs must be **independent** (no cross-references; no learning between attempts).

### Step 5: Gate check (variation audit)
Do not proceed to full plans until this audit passes:
- Each “must vary” axis **actually varies** across the briefs.
- Each brief makes **one coherent choice** per varied axis (no “generic adapter that supports everything” unless that is the *explicit* option being evaluated).
- Frozen axes remain consistent across briefs.

If the audit fails:
- Regenerate the failed brief(s) rather than “refining” them.

### Step 6: Expand briefs into full plans
Only after the user approves the set of attempt briefs:
- Generate the full implementation plans (staged), one per attempt.
- Carry the chosen axis options through the stages with no backsliding into genericity.

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
