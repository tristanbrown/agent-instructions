# AGENTS.AXES.md
[//]: # (DO NOT EDIT LOCALLY - this file is maintained in the agent-instructions repo and synced.)

---

## Axes of Variation Discovery (Creative Stack)

### Goal
Axis discovery surfaces **orthogonal axes of variation** in a spec before commitments, constraints, or structure collapse the space.
It's not an exhaustive list of parameters.

---

## Protocol

### Step 1: Run axis generators (independent prompts)
Run each generator as its own prompt/pass. They are not sequential steps; do not "chain" results.

#### Generator A: Conceptual Inversion
Prompt:
- "If this system were designed with the **opposite priorities**, what would change?"

Extraction rule:
- Turn each thing that would change under opposite priorities into one or more axes.

#### Generator B: Responsibility Reassignment
Prompt:
- "Which object **owns** this decision or transformation instead?"

Extraction rule:
- Turn each ownership shift into an axis about **where the boundary lives**.

#### Generator C: Failure-Mode-First Enumeration
Prompt:
- "How could this go wrong in ways that **force a redesign**?"

Extraction rule:
- Enumerate distinct failure modes (stress cases) as outputs.
- Do not try to solve the failures here! Only identify the axes that lead into failures!

#### Generator D: Analogy Hopping
Prompt:
- "What existing systems solve a similar problem differently?"

Extraction rule:
- For each analogy, translate the different approaches of that system into axes for the current system.

### Step 2: Merge and normalize
- Merge outputs across generators.
- Deduplicate by **collapsing synonymous axes** and splitting "combo axes" into atomic ones.
- Drop axes that only vary superficial parameters.

### Step 3: Classify each axis by decision class (and pick resolution)
Assign exactly one decision class per axis:

**Value Judgment**
- Question: "Which outcome do we want?"
- Resolution: interactive discussion (humans decide).

**Structural Uncertainty**
- Question: "What shapes even exist, and which ones survive contact with reality?"
- Resolution: Skeleton Spikes (shape probes).

**Mechanism Uncertainty**
- Question: "Which mechanism works better once structure is fixed?"
- Resolution: compare mechanisms within one fixed structure (local experimentation).

**External Capability Uncertainty**
- Question: "What do our tools/models actually do well or poorly?"
- Resolution: targeted, depth-first probes / one-shot trials.

**Noise / Premature Optimization**
- Question: "This feels like a decision, but probably isn't yet."
- Resolution: explicit deferral.

---

## Output format
- Plain markdown.
- One axis per bullet, assigned to Decision Class categories
