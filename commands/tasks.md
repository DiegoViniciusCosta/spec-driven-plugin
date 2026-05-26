---
name: tasks
description: Phase 3 — CREATE TASKS: break an approved plan into atomic, testable tasks
argument-hint: <NNN-slug feature folder>
---

You are executing **Phase 3 (CREATE TASKS)** of the spec-driven framework.

Target feature: $ARGUMENTS

## Pre-checks (run first, abort if any fails)

1. Verify `.spec/$ARGUMENTS/spec.md` and `.spec/$ARGUMENTS/plan.md` both exist. If either is missing, tell the user which phase to run and stop.
2. Read both **in full**.
3. Skim any docs referenced by the plan (`.spec/docs/*.md`).

## What to do

1. Invoke the `spec-driven` skill so its references are available.
2. Read `references/create-tasks.md` from the skill and follow the atomicity rules **strictly**.
3. Create the `tasks/` subfolder inside `.spec/$ARGUMENTS/` if it doesn't exist.
4. Write one `.md` file per task using the required format. Each task must have:
   - A single observable outcome
   - At least one runnable verification command
   - The atomicity check filled in
5. List all created tasks for the user to review.
6. Wait for the user to say "tasks approved" (or equivalent).

## Hand-off

After approval, tell the user **verbatim**:

> N tasks created under `.spec/$ARGUMENTS/tasks/`. For context isolation, open a fresh session per task and run `/execute $ARGUMENTS TASK-NNN`.

Do **not** start executing tasks in this session.
