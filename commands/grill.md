---
name: grill
description: Cross-cutting tool — run a clarifying interview when clarity is missing
argument-hint: <topic or what is unclear>
---

You are running the **GRILL** tool from the spec-driven framework.

Topic: $ARGUMENTS

## What to do

1. Invoke the `spec-driven` skill so its references are available.
2. Read `references/grill.md` from the skill and follow it **strictly**:
   - One question at a time, always with a recommended answer.
   - Read the code instead of asking when the answer is discoverable there.
   - Update `.spec/CONTEXT.md` (via `references/context.md`) and create docs (via `references/doc.md`) **inline** as decisions crystallise — never batch.
3. If a session log makes sense, write it at `.spec/<active-feature>/grill.md`.

## Hand-off

GRILL does not produce a spec, plan, or implementation. When the user is satisfied, tell them:

> Clarity established. Return to the phase you came from (`/spec`, `/plan`, `/tasks`, or `/execute`) — ideally in a fresh session.
