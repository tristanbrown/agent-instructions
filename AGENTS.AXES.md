# AGENTS.AXES.md
[//]: # (DO NOT EDIT LOCALLY - this file is maintained in the agent-instructions repo and synced.)

---

## Axes of Variation Discovery (Creative Stack)

### Goal
Axis discovery is not about enumerating all options.
It is about maximizing coverage of **orthogonal ways the design space can bend** before early commitments collapse it.

### Core rule
Do not use a single brainstorm pass.
Run **separate generator passes** and merge the results.

---

## Protocol

### Step 0: Setup (from the spec)
- Extract the spec's **invariants** (requirements that must not change across variants).
- Create an "Axis Scratchpad" and capture candidate axes as:
  - **Axis:** short name
  - **Question:** what decision is being made?
  - **Poles:** the concrete alternatives
  - **Impact:** what would change if you flipped poles? (1 line)

### Step 1: Conceptual inversion (primary generator)
Prompt:
- "If this system were designed with the **opposite priorities**, what would change?"

How to use:
- Identify implied priorities (simplicity vs power, local vs global, eager vs lazy, immutable vs mutable, etc.).
- Flip them deliberately, then extract the resulting decisions as axes.

### Step 2: Responsibility reassignment (structure generator)
Prompt:
- "Who **owns** this decision or transformation instead?"

How to use:
- Locate key transformations/decisions in the spec.
- Reassign ownership across boundaries (core vs edge, producer vs consumer, caller vs callee, user vs system).
- Convert each reassignment into an axis about **where the boundary lives**.

### Step 3: Failure-mode-first enumeration (stress generator)
Prompt:
- "How could this go wrong in ways that **force a redesign**?"

How to use:
- Enumerate plausible failure modes, then ask: "What architectural choice would make this failure easy vs hard?"
- Convert each such choice into an axis (retries, ordering, idempotency, drift, partial failure, etc.).

### Step 4: Analogy hopping (late-stage broadener)
Prompt:
- "What existing systems solve a similar problem differently?"

How to use:
- Name 3-5 analog domains and import their structural primitives.
- Translate the imported alternative decomposition into axes (compiler pass vs pipeline, diff/patch vs event log, stream vs batch, etc.).

### Step 5: Merge and normalize
- Merge scratchpad outputs across generators.
- Deduplicate by **collapsing synonymous axes** and splitting "combo axes" into atomic ones.
- Drop axes that only vary superficial implementation detail (rename, minor library swaps without architectural consequence).

### Step 6: Classify each axis by variation role
Assign exactly one role per axis:

**Decide Upfront**
- Must be aligned interactively because mixing choices would make attempts incomparable or invalidate shared evaluation.

**Vary Across Attempts**
- Safe to select independently per attempt; differences remain comparable and evaluable.

**Deferred**
- Can be stubbed or postponed without constraining later architectural choices.

Keep **Decide Upfront** sparse: only for decisions that reshape all variants.

---

## Output format
- Plain markdown.
- One axis per bullet, using this schema:
  - `Axis:` ...
  - `Question:` ...
  - `Poles:` ...
  - `Role:` Decide Upfront | Vary Across Attempts | Deferred
  - `Impact:` ...

