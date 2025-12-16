# AGENTS.ATTEMPTS.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Axis of Variation Discovery Protocol

Use this protocol when you want multiple plans/implementations, but it is unclear which architectural choices are the high-leverage ones worth varying across attempts.

### Output: a "Variation Contract"
Before generating any attempts, produce a short, explicit "Variation Contract" that locks in what will and will not vary across attempts.

The contract must include:
- **Must-vary axes (2-4 max):** the only choices that attempts are required to differ on.
- **Frozen axes (5-10):** choices that must remain constant to prevent noisy differences.
- **Stage-1 commitments:** decisions required to make Stage 1 runnable/testable, plus how to handle them if intentionally deferred.

### Step 1: Identify candidate axes (broad sweep)
From the spec(s), list candidate axes implied by the work. Prefer axes that affect:
- Core data abstractions and boundaries
- External integrations
- Persistence strategy when relevant
- Testability and determinism

Do **not** treat these as axes unless explicitly required by the spec:
- Interface surface choices
- Production/ops concerns
- Minor preferences

### Step 2: Rank axes by leverage (pick the real knobs)
For each candidate axis, score it qualitatively (low/med/high) on:
- **Blast radius:** how many modules/stages are affected
- **Switching cost:** how hard it is to change later without rework
- **Uncertainty:** how likely you’ll learn you picked wrong
- **Spec coupling:** how strongly the spec pushes toward one option
- **Risk:** chance of dead-ends, brittle abstractions, or untestable stages

Select **2-4** axes with the highest combined leverage as **Must-vary**.
Select **5-10** axes to **Freeze** (choose a default and hold it constant).

### Step 3: Define allowed values for each must-vary axis (avoid combinatorics)
For each must-vary axis:
- Define **2-4 mutually exclusive settings**.
- Define the **primary constraint** each setting optimizes for.
- Define the **minimum viable contract boundary** (what must remain stable across stages/attempts).

Rule against combinatorial explosion:
- Attempts should differ primarily on **one** must-vary axis each.
- Do not attempt to cover every combination of settings.

### Step 4: Stage-1 commitments (make plans concrete)
List all decisions required for Stage 1 to be runnable/testable. For each item:
- Either (A) **Commit** to a concrete default, or
- (B) **Defer with a spike**: add an explicit spike stage with success criteria and an artifact, and require a local substitute so later stages remain testable without the real integration.

### Step 5: Attempt generation rules (binding)
Once you have a Variation Contract:
- Each attempt must begin with an **Assumptions / Commitments** section that instantiates the contract.
- If an attempt uses a "generic adapter" for a must-vary axis, it must still include a **single concrete reference implementation** (for testability) and explicitly state what is deferred and why.
- If multiple attempts converge on the same choice for a must-vary axis, stop and revise the Variation Contract or regenerate attempts.

### Step 6: When to run this protocol
Run Axis of Variation Discovery when:
- Parallel attempts differed mainly in low-stakes details, or
- Important architectural choices were left underspecified, or
- Plans share the same unexamined defaults without justification.

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
