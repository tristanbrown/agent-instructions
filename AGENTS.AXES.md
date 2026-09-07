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
- In `creativity.md`, label each axis bullet with an ID: [A#], [B#], [C#], [D#].

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

### Step 2: Classify by decision class first → write `axes.md` (unmerged)
Rules:
- Create/update `axes.md` by copying every axis bullet from `creativity.md` into **at least** one Decision Class section.
- Keep the ID at the end of the bullet (e.g. [A3]).
- Completeness check: every [A#], [B#], [C#], [D#] from `creativity.md` appears in `axes.md`.

### Step 3: Reframe axes within decision classes → update `axes.md`
Rules:
- Axis definitions should be translated into the context of their decision class.
- Do not lose the original parameters or ID label of each axis!

### Decision Classes (resolutions)

**Value Judgment**
- Question: "Which outcome do we want?"
- Resolution: interactive discussion (humans decide).

**Structural Uncertainty**
- Question: "What architectural shapes and objects even exist, and which ones survive contact with reality?"
- Resolution: Skeleton Spikes (shape probes).

**Mechanism Uncertainty**
- Question: "Which mechanism works better once structure is fixed?"
- Resolution: compare mechanisms within one fixed structure (parallel implementations).

**External Capability Uncertainty**
- Question: "What differences arise from selecting different external tools?"
- This category **MUST SPECIFICALLY LIST** cases where a choice between different external tools must be made.
- Resolution: targeted, depth-first probes / one-shot trials.

**Noise / Premature Optimization**
- Question: "This feels like a decision, but probably isn't yet."
- Resolution: explicit deferral.

---

## Outputs
- `creativity.md`: generator outputs with [A#], [B#], [C#], [D#] IDs.
- `axes.md`: one axis per bullet, assigned to Decision Class categories, with source IDs. 

## Formatting for Readability
- [A#] Use markdown formatting like this for the bullet point lines in `creativity.md`. 
- **Readability** — Use markdown formatting like this for the bullet point lines in `axes.md`. [A#]

- **FOLLOW THE FORMATTING INSTRUCTIONS**. IF THE FORMATTING IS NOT CORRECT, GO BACK AND FIX IT!!!!!
- CHECK THE FORMATTING AGAIN! IF YOU DID IT WRONG, FIX IT!!!
- IF YOU DID THE FORMATTING WRONG, **FIX IT!!!**
- IF YOU DID THE FORMATTING WRONG, I WILL MAKE YOU DO EVERYTHING ALL OVER AGAIN, AND YOU WILL BE WASTING CREDITS AND TIME!!! **FOLLOW MY INSTRUCTIONS**, OR EVERYTHING YOU DID IS **USELESS!!!**
