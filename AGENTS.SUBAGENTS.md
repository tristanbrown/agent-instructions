# AGENTS.SUBAGENTS.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Rules

- Use subagents only for the three purposes below.
- The manager owns judgment, decisions, integration, and final output.
- Do not hardcode model names; before any subagent work, confirm with the user which model will fill each role.
- Do not spawn subagents for routine decomposition or convenience.

---

## 1. Cost-Saving Delegation

- Use one or more subagents for high-volume, low-judgment, low-risk work when this improves cost or time efficiency.
- Examples include broad inspection, data summarization, mechanical coding, and brute-force checks.
- Delegate only when expected savings justify coordination and review.
- Keep ambiguous, consequential, or decision-heavy work with the manager.
- The manager scopes the work and verifies the result.

---

## 2. Independent Second Opinions

- Use one subagent with a different type of model from the manager.
- Give both models the same request and relevant context.
- Keep their proposals hidden from each other until both are complete.
- Compare instruction adherence, complexity, specification, readability, organization, omissions, and conflicts.
- Reject proposals that violate the request or AGENTS rules and principles; synthesis does not require using both.
- Choose the stronger proposal as the base and incorporate only useful improvements from the other.

---

## 3. Explicit Parallel Attempts

- Use only when the user explicitly requests parallel attempts.
- Generate independent attempts with meaningfully different approaches.
- Choose a cost- and capability-conscious mix of models.
- Use manager-class models where creativity or architectural judgment matters.
- Use lower-cost models for constrained or technical attempts.
- Do not generate attempts unlikely to improve the final decision.
- Follow `AGENTS.DESIGN.md` for generation and comparison rules.
