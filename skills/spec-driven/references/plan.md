# Phase 2 — PLAN

With the spec approved, design the technical approach.

## What to do
1. Analyze the spec and define the implementation strategy.
2. Write the plan to `.spec/NNN-descriptive-slug/plan.md` (same feature folder as the spec) using the format below.
3. Wait for approval before creating tasks.

## Plan format

```
## PLAN: [Feature or Change Name]

### Approach
[Describe the chosen technical strategy and why, in 2–5 sentences.]

### Stack involved
- [Layer/component]: [files, modules, patterns affected]
- Integration: [APIs, contracts, serialization]

### Delivery sequence
1. [Whatever unblocks the rest comes first]
2. [Then...]
3. ...

### Dependencies between tasks
[Describe which tasks depend on others, if any.]

### Technical decisions
| Decision | Chosen option | Reason | Doc |
|----------|--------------|--------|-----|
| [e.g. persistence] | [e.g. JPA Repository] | [e.g. already the project standard] | — |
| [hard-to-reverse decision] | [chosen] | [short reason] | [DOC-NNNN](../docs/NNNN-...md) |

> Hard-to-reverse, surprising, or trade-off-heavy decisions belong in a **doc** under `.spec/docs/` (see `references/doc.md`). Reference the doc here; do not duplicate its reasoning.

### Risks and mitigations
| Risk | Likelihood | Mitigation |
|------|-----------|------------|
| [e.g. breaking API change] | Medium | [e.g. version the endpoint] |
```

## Rules
- The plan must be derived from the spec, not from your assumption of what the user wants.
- Prefer the simplest approach that satisfies the acceptance criteria.
- If domain terms feel fuzzy, invoke **GRILL** (`references/grill.md`) before finalising the plan.
- For each new or refined domain term, update `.spec/CONTEXT.md` via `references/context.md`.
- For each hard-to-reverse decision, create a **doc** via `references/doc.md` and reference it in the table above.
- Only advance after the user confirms: "plan approved" or equivalent.
