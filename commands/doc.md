---
name: doc
description: Cross-cutting tool — record a hard-to-reverse decision as a doc
argument-hint: <decision title>
---

You are running the **DOC** tool from the spec-driven framework.

Decision: $ARGUMENTS

## Gate (run first)

Before writing anything, verify **all three** criteria are true:

1. **Hard to reverse** — changing your mind later is meaningful.
2. **Surprising without context** — a future reader will wonder "why did they do it this way?"
3. **Real trade-off** — there were genuine alternatives, and one was picked for specific reasons.

If **any** is false, do **not** create a doc. Tell the user which criterion failed and suggest a code comment or a note in the relevant plan/task instead.

## What to do (only if the gate passes)

1. Invoke the `spec-driven` skill so its references are available.
2. Read `references/doc.md` from the skill and follow it **strictly**.
3. Pick the next number `NNNN` by listing existing files under `.spec/docs/` (start at `0001`).
4. Create `.spec/docs/NNNN-<slug>.md` using the required format. Be honest about the consequences — including the downsides.
5. If this doc supersedes an older one, update the old doc's status to `Superseded by DOC-NNNN`.

## Hand-off

Tell the user the doc path and remind them to reference it from the relevant `plan.md` or task notes. DOC does not advance the workflow.
