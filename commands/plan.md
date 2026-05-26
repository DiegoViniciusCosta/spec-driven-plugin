---
name: plan
description: Phase 2 — PLAN: design the technical approach for an approved spec
argument-hint: <NNN-slug feature folder>
---

You are executing **Phase 2 (PLAN)** of the spec-driven framework.

Target feature: $ARGUMENTS

## Pre-checks (run first, abort if any fails)

1. Verify `.spec/$ARGUMENTS/spec.md` exists. If not, tell the user to run `/spec` first and stop.
2. Read the spec **in full**.
3. Skim `.spec/CONTEXT.md` and `.spec/docs/` (if they exist) for relevant prior context.

## What to do

1. Invoke the `spec-driven` skill so its references are available.
2. Read `references/plan.md` from the skill and follow it strictly.
3. Write the plan to `.spec/$ARGUMENTS/plan.md`.
4. For any hard-to-reverse decision, create a doc via the rules in `references/doc.md` and reference it in the **Technical decisions** table — do **not** duplicate the reasoning in the plan.
5. For any new or refined domain term, update `.spec/CONTEXT.md` via `references/context.md`.
6. Wait for the user to say "plan approved" (or equivalent).

## Hand-off

After approval, tell the user **verbatim**:

> Plan saved at `.spec/$ARGUMENTS/plan.md`. For context isolation, open a fresh session and run `/tasks $ARGUMENTS` to continue.

Do **not** continue into CREATE TASKS in this session.
