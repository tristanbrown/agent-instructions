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

### Step 1: Run axis generators (independent prompts)
Run each generator as its own prompt/pass. They are not sequential steps; do not "chain" results mid-pass.

#### Generator A: Conceptual inversion
Prompt:
- "If this system were designed with the **opposite priorities**, what would change?"

Extraction rule:
- Turn each flipped priority into one or more axes (with concrete poles).

#### Generator B: Responsibility reassignment
Prompt:
- "Who **owns** this decision or transformation instead?"

Extraction rule:
- Turn each ownership shift into an axis about **where the boundary lives**.

#### Generator C: Failure-mode-first enumeration
Prompt:
- "How could this go wrong in ways that **force a redesign**?"

Extraction rule:
- For each failure mode, derive the architectural choice that makes it easy vs hard, then record that choice as an axis.

#### Generator D: Analogy hopping
Prompt:
- "What existing systems solve a similar problem differently?"

Extraction rule:
- Import an alternative decomposition from the analogy, then translate it into axes.

### Step 2: Merge and normalize
- Merge outputs across generators.
- Deduplicate by **collapsing synonymous axes** and splitting "combo axes" into atomic ones.
- Drop axes that only vary superficial implementation detail.

### Step 3: Classify each axis by decision class (and pick resolution)
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
