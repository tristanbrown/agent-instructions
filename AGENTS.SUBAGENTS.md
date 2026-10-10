# AGENTS.SUBAGENTS.md
[//]: # (DO NOT EDIT LOCALLY — this file is maintained in the agent-instructions repo and synced.)

---

## Rules

- Use subagents only for the three purposes below.
- Subagents provide inputs; the manager owns judgment, integration, and final output within the user-directed workflow.
- Before any subagent work, confirm with the user which model will fill each role, except in a limited set of cases:
  - test-suite execution

---

### 1. Cost-Saving Delegation

- Use one or more subagents for high-volume, low-judgment, low-risk work when this improves cost or time efficiency.
- Examples include broad inspection, data summarization, mechanical coding, and brute-force checks.
- Delegate test-suite execution.
- Limit test duration and output.
- Delegate only when expected savings justify coordination and review.
- Keep ambiguous, consequential, or decision-heavy work with the manager.
- The manager scopes the work and verifies the result.

---

### 2. Independent Reviews

- Use one or two subagents with model types different from the manager and each other.
- Give each model the same request and relevant context.
- Keep their proposals hidden from each other until all are complete.
- Compare instruction adherence, complexity, specification, readability, organization, omissions, and conflicts.
- Reject proposals that violate the request or AGENTS rules and principles; synthesis does not require using every proposal.
- Choose the strongest proposal as the base and incorporate only useful improvements from the others.

---

### 3. Explicit Parallel Attempts

- Use only when the user explicitly requests parallel attempts.
- Generate independent attempts with meaningfully different approaches.
- Choose a cost- and capability-conscious mix of models.
- Use manager-class models where creativity or architectural judgment matters.
- Use lower-cost models for constrained or technical attempts.
- Do not generate attempts unlikely to improve the final decision.
- Follow `AGENTS.DESIGN.md` for generation and comparison rules.

---

## Model Roles

### Defaults

- **Cost-saving delegation:** Use `gpt-6-luna` with `max` reasoning effort.
- **Independent second opinion:** Use `gpt-6-luna` with `max` reasoning effort.
- **Independent third opinion:** Use `gpt-6.1-sol` with `xhigh` reasoning effort.
- **Parallel implementation attempts:** Prefer `gpt-6-luna` with `max` reasoning effort.

---

### Fallbacks

- Do not substitute fallback models.
- If the assigned model is unavailable, try again.
- If it remains unavailable, consult the user before proceeding.
