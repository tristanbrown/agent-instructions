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
- Identify stated and implied priorities.
- Flip them deliberately, then extract the resulting decisions as axes.

### Step 2: Responsibility reassignment (structure generator)
Prompt:
- "Who **owns** this decision or transformation instead?"

How to use:
- Locate key transformations/decisions in the spec.
- Reassign ownership across boundaries and layers.
- Convert each reassignment into an axis about **where the boundary lives**.

### Step 3: Failure-mode-first enumeration (stress generator)
Prompt:
- "How could this go wrong in ways that **force a redesign**?"

How to use:
- Enumerate plausible failure modes, then ask: "What architectural choice would make this failure easy vs hard?"
- Convert each such choice into an axis.

### Step 4: Analogy hopping (late-stage broadener)
Prompt:
- "What existing systems solve a similar problem differently?"

How to use:
- Name a few analog domains and import their structural primitives.
- Translate the imported alternative decomposition into axes.

### Step 5: Merge and normalize
- Merge scratchpad outputs across generators.
- Deduplicate by **collapsing synonymous axes** and splitting "combo axes" into atomic ones.
- Drop axes that only vary superficial implementation detail.

### Step 6: Classify each axis by decision class (and pick resolution)
Assign exactly one decision class per axis:

**Value Judgment**
- Question: "Which outcome do we want?"
- Resolution: interactive discussion (humans decide).

**Structural Uncertainty**
- Question: "What shapes even exist, and which ones survive contact with reality?"
- Resolution: skeleton spikes (shape probes).

**Mechanism Uncertainty**
- Question: "Which mechanism works better once structure is fixed?"
- Resolution: compare mechanisms within one fixed structure (local experimentation).

**External Capability Uncertainty**
- Question: "What do our tools/models actually do well or poorly?"
- Resolution: targeted probes / one-shot trials.

**Noise / Premature Optimization**
- Question: "This feels like a decision, but probably isn't yet."
- Resolution: explicit deferral (with a reminder trigger).

---

## Output format
- Plain markdown.
- One axis per bullet, using this schema:
  - `Axis:` ...
  - `Question:` ...
  - `Poles:` ...
  - `Decision Class:` Value Judgment | Structural Uncertainty | Mechanism Uncertainty | External Capability Uncertainty | Noise / Premature Optimization
  - `Resolution:` Interactive discussion | Skeleton spikes | Local experimentation | Targeted probe | Defer
  - `Impact:` ...
