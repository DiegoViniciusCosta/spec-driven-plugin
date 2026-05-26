---
name: execute
description: Phase 4 — EXECUTE: implement a single approved task
argument-hint: <NNN-slug> <TASK-NNN>
---

You are executing **Phase 4 (EXECUTE)** of the spec-driven framework.

Arguments: $ARGUMENTS (expected format: `NNN-slug TASK-NNN`)

## Pre-checks (run first, abort if any fails)

1. Parse $ARGUMENTS into the feature slug and the task ID.
2. Find the task file at `.spec/<slug>/tasks/<TASK-ID>-*.md`. If not found, list the available tasks in that folder and stop.
3. Read the task file **in full**, including preconditions and verification commands.
4. Verify task `Status` is not already `[x] Done`. If it is, tell the user and stop.
5. Verify all `Depends on` tasks are marked `[x] Done`. If not, list the unfulfilled dependencies and stop.
6. Skim `.spec/CONTEXT.md` and any docs referenced by the task's plan.

## What to do

1. Invoke the `spec-driven` skill so its references are available.
2. Read `references/execute.md` from the skill and follow it **strictly**.
3. Implement **only** the scope of this task. If you spot work outside scope, create a new task file and report it — do not implement.
4. If you hit a conceptual ambiguity, stop and propose `/grill`.
5. If a new domain term emerges, update `.spec/CONTEXT.md` via `references/context.md`.
6. If a hard-to-reverse decision arises that wasn't planned, create a doc via `references/doc.md` and link it from the task's notes.
7. Run the verification command(s) from the task file. Only mark `Status: [x] Done` if they pass.
8. Report what was done, what was verified, and stop.

## Hand-off

After completion, tell the user **verbatim**:

> TASK-NNN done and verified. For context isolation, open a fresh session and run `/execute <slug> TASK-<next>` for the next task.

Do **not** start the next task in this session.
