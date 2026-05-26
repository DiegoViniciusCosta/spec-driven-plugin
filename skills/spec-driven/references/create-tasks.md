# Phase 3 — CREATE TASKS

With the plan approved, break the delivery into **atomic, executable, individually testable** tasks.

## Atomicity principle

**One task = one observable behavior change, verifiable by one concrete command.**

A task is atomic when:
- It has **a single reason to change** (one purpose, one outcome).
- It can be **executed in isolation** — no need to do "the next one" for this one to make sense.
- It can be **verified in isolation** — there is at least one runnable command that proves it works.
- It can be **reverted in isolation** — rolling it back does not break previous tasks.

If any of the four fails, the task is not atomic. Split it.

## What to do
1. Create a `tasks/` subfolder inside the feature folder: `.spec/NNN-descriptive-slug/tasks/`.
2. Create one `.md` file per task using the format below.
3. List the created tasks for the user to review.
4. Wait for approval before executing any of them.

## File naming
```
.spec/NNN-descriptive-slug/tasks/
  TASK-001-[descriptive-slug].md
  TASK-002-[descriptive-slug].md
  ...
```
Example: `.spec/001-user-registration/tasks/TASK-001-create-users-table.md`

## Task format

```markdown
# TASK-[NNN]: [Clear, direct title — one verb, one object]

**Status:** [ ] Pending | [ ] In progress | [x] Done
**Plan phase:** [Plan sequence number]
**Depends on:** TASK-[NNN] | None
**Stack:** [stack/layer name]
**Estimated size:** XS (<50 LOC) | S (<100) | M (<200). If larger, split.

## Goal
[One sentence: the single observable change this task delivers.]

## Context
[Why does this task exist? Which part of the spec/plan does it satisfy?]

## Preconditions
[What must already be true before this task runs: previous tasks done, fixtures present, env vars set, migrations applied. List explicitly.]

## Files to create or modify
- `[path/to/file]` — [what changes]
- `[path/to/file]` — [what changes]

## Implementation steps
1. [Concrete, verifiable step]
2. [Concrete, verifiable step]
3. ...

## Observable outcome
[What changes in the system after this task is done, in a way someone can see/measure. Examples: "endpoint POST /users returns 201", "column `email_verified` exists in `users` table", "button renders on login screen".]

## How to verify
[At least one concrete command or action, with the expected result. This is the proof that the task works in isolation.]

Examples:
- `./gradlew test --tests UserRegistrationServiceTest` → all green
- `curl -X POST localhost:8080/users -d '{...}'` → returns `201 Created` with `{"id": "..."}`
- Open `/login`, click "Sign up" → form appears with fields X, Y, Z

## Completion criteria
- [ ] Observable outcome is true
- [ ] Verification command passes
- [ ] No regressions in adjacent modules (state which ones you checked)
- [ ] Code review checklist done (if applicable)

## Atomicity check (fill before submitting for approval)
- [ ] This task has a single reason to change
- [ ] The title has no "and" / "with" / "plus" coupling two things
- [ ] It can be reverted without breaking previous tasks
- [ ] It can be verified without running any later task

## Notes
[Known pitfalls, local decisions, useful references. Leave empty if none.]
```

## Rules
- One task = one unit of work that can be reviewed, merged, and reverted in isolation.
- **Single reason to change:** if the task does two things, it's two tasks. Example: "create table AND seed data" → split.
- **No "and" coupling in titles:** "Create endpoint and add auth and log metrics" = three tasks.
- Avoid tasks expected to exceed ~200 lines of code. If it gets large, split it.
- Every task must have at least one verification command in **How to verify**. If you cannot write one, the task is too abstract — refine it.
- Never mix unrelated layers in the same task unless they are inseparable.
- For brownfield: the first task should always be "map impact on existing code" if that hasn't been done yet.

## Splitting heuristics (when in doubt, split)

| Smell | Likely split |
|-------|--------------|
| Title contains "and", "with", "plus", "+" | Two tasks |
| Verification needs more than one command of different nature | Two tasks |
| Touches schema + business logic + UI in one go | Three tasks (schema → logic → UI) |
| Has more than ~5 implementation steps | Probably two tasks |
| Cannot be reverted without manual cleanup | Split the irreversible part out |
| Requires a feature flag to ship safely | The flag setup is its own task |

## Atomic vs. inflated — quick examples

**Inflated (bad):**
```
TASK-001: Implement user registration
  - Create users table
  - Add User entity and repository
  - Create POST /users endpoint
  - Send confirmation email
  - Add registration form on frontend
```
This is 5 tasks pretending to be one. It cannot be verified, reviewed, or reverted in isolation.

**Atomic (good):**
```
TASK-001: Create users table migration
TASK-002: Add User entity and repository
TASK-003: Expose POST /users endpoint (no email yet)
TASK-004: Send confirmation email on user creation
TASK-005: Add registration form on login screen
```
Each one has a single observable outcome, can be tested standalone, and can be reverted independently.
