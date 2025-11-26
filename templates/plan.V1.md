# <Feature or Module Name> – Implementation Plan V1 
<across attempts, increment the version number in the header and filename>

## Strategy

Summarize this plan in a few sentences, explaining what is unique about it. Be specific about key objects/classes!

---

## Outline

**Stage 1:** Short, 1-line summary.
**Stage 2:** Short, 1-line summary.
...
**Stage N:** Short, 1-line summary.

---

## Stage 1. <Descriptive Name>

**Goal:** What this stage accomplishes in the project.

**Scope:**
- Short bullet list of the concepts that are implemented in this stage.
- Aim for 3 lines, 60-100 characters.

**Implementation Decisions:**
- Bullet list of the key, high-level technical and architectural choices.
- Name key objects/classes, their role, and how they are represented.
- Make concrete decisions about *concepts* and *technologies*, but don't constrain implementation!

Match the style and level of detail in this example:
- Use Python models (dataclasses or Pydantic-style) for:
  - `RawDocument` (id, source type such as `amazon_api` or `web_review`, ASIN, URL or origin, text or structured payload, timestamps).
  - `NormalizedProduct` (ASIN, title, brand, price, rating, key specs, review summary, attribute-level provenance).
- Implement a `ClassName` that:
  - Accepts a list of IDs as input and maps `OtherObject` onto them.
  - Stores IDs as an attribute for later reference.
  - Uses AI-based summarization to convert `OtherObject` into `OutputObject` for each input value.
- Keep all processing in-memory for this story; no persistent database is introduced yet.
- Ensure the final output is a list of `OutputObject` items with stable ordering.

REMEMBER:
- Do not give function signatures! Do not name variables, fields, or parameters! Do not use type hints!

**Acceptance Criteria:**
- Bullet list, in natural language, of the observable outcomes or behaviors that I, the human developer, need to manually test and evaluate.
- Be specific!
- Still no pseudocode.

---

## Stage 2. <Descriptive Name>

...

---

## Stage N. <Descriptive Name>

(Repeat the above structure for each implementation stage.)
