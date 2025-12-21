# AGENTS.ATTEMPTS.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Axis of Variation Discovery Protocol

Use this protocol before generating multiple attempts when the important variation axes are unclear or underspecified.

1. **List candidate axes of variation**
   - Identify 3-7 major decision axes that materially change architecture or implementation plan shape.
   - Prefer high-impact axes (core abstractions, data model, integration strategy) over minor details.

2. **Classify each axis**
   - **Fixed upfront**: must be decided before planning.
   - **Varied across attempts**: each attempt must take a different stance.
   - **Deferred**: keep a minimal seam and defer the decision.

3. **Constrain the variation budget**
   - Vary only 2-3 axes across attempts.
   - Hold everything else constant to avoid combinatorial noise.

4. **Confirm with the user**
   - Present the axis list and classifications briefly.
   - Do not proceed with attempts until the user confirms or edits the list.

5. **Enforce during plan writing**
   - Each attempt must explicitly state its stance on the varied axes.
   - Any axis marked Fixed must not diverge across attempts.
   - Any axis marked Deferred must include a minimal seam and a note for later decision.

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
