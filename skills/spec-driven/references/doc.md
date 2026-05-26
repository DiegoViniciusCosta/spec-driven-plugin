# DOC — record an important decision (cross-cutting tool)

A **doc** captures a decision that future readers will need to understand. Docs live under `.spec/docs/` and are shared across the project (not scoped to a single feature).

**Not a phase.** Create a doc whenever an important decision is made — during GRILL, PLAN, EXECUTE, or any time a real trade-off is resolved.

## When to create a doc

Create a doc **only when all three are true**:

1. **Hard to reverse** — changing your mind later is meaningful (data model choices, public contracts, framework picks, security boundaries).
2. **Surprising without context** — a future reader will wonder "why did they do it this way?"
3. **Real trade-off** — there were genuine alternatives and one was picked for specific reasons.

If any of the three is missing, **don't create a doc.** Trivial, reversible, or obvious choices don't need one. Docs are precious — over-documenting devalues them.

When in doubt, ask: "Would a new contributor in 6 months be confused by this choice?" If no, skip.

## File location and naming

```
.spec/
  docs/
    0001-event-sourced-orders.md
    0002-postgres-for-write-model.md
    0003-soft-delete-strategy.md
```

- Numbering is sequential and zero-padded (`0001`, `0002`, ...). Pick the next number by looking at existing files.
- Slug is short and descriptive — names the decision, not the feature that motivated it.
- Create the `docs/` folder lazily — only when writing the first doc.

## Format

```markdown
# DOC NNNN: [Decision title]

**Status:** Proposed | Accepted | Superseded by DOC-XXXX
**Date:** YYYY-MM-DD

## Context
[What forces are at play? Why does this decision need to be made now?]

## Decision
[What was decided, in one or two sentences.]

## Alternatives considered
- [Option A] — rejected because [reason]
- [Option B] — rejected because [reason]

## Consequences
[What becomes easier, what becomes harder, what is now locked in. Be honest about the downsides.]
```

## Linking from other artifacts

- From a feature `plan.md`, reference docs in the **Technical decisions** table.
- From `.spec/CONTEXT.md`, do **not** link to docs — the glossary stays free of decisions.
- From code comments, link to docs only when the *why* genuinely can't fit in a short comment.

## Lifecycle

- Docs are append-only in spirit. To revise a decision, write a **new doc** that supersedes the old one and update the old one's status to `Superseded by DOC-NNNN`.
- Never silently rewrite an accepted doc — git history is not enough; the supersession chain is part of the story.
