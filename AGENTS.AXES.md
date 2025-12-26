# AGENTS.AXES.md
[//]: # (DO NOT EDIT LOCALLY - this file is maintained in the agent-instructions repo and synced.)

---

## Axes of Variation Discovery (Creativity Stack)

### Goal
Axis discovery surfaces **orthogonal axes of variation** in a spec before commitments, constraints, or structure collapse the space.
It's not an exhaustive list of parameters.

---

## Protocol

### Step 1: Run axis generators (independent prompts) → write `creativity.md`
Run each generator as its own prompt/pass. They are not sequential steps; do not "chain" results.

Rules:
- Write generator outputs to `creativity.md` before doing any merge/classification.
- In `creativity.md`, label each axis bullet with an ID: `A1…`, `B1…`, `C1…`, `D1…`.

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

### Step 2: Merge and normalize → write `axes.md`
- Merge outputs across generators.
- Deduplicate by collapsing synonymous axes, but keep any distinct options/variants (don’t “dedupe away” real choices).
- In `axes.md`, each axis bullet must include the source IDs in brackets (e.g. `[A2, C4]`).
- Completeness check: every `A# / B# / C# / D#` from `creativity.md` appears in at least one `axes.md` axis bullet.

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
- Resolution: compare mechanisms within one fixed structure (parallel implementations).

**External Capability Uncertainty**
- Question: "What do the available tools actually do well or poorly?"
- Resolution: targeted, depth-first probes / one-shot trials.

**Noise / Premature Optimization**
- Question: "This feels like a decision, but probably isn't yet."
- Resolution: explicit deferral.

---

## Output format
- `creativity.md`: generator outputs with `A# / B# / C# / D#` IDs.
- `axes.md`: one axis per bullet, assigned to Decision Class categories, with source IDs. Use markdown formatting for readability.
