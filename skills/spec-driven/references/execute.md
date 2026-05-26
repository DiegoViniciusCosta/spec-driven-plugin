# Phase 4 — EXECUTE

With the tasks approved, implement them one at a time.

## What to do
1. Ask the user which task to execute first (or follow the plan sequence if there's no preference).
2. Implement **only** the scope of the active task.
3. When done, mark the status as `[x] Done` in the task's `.md` file.
4. Report what was done and wait for instruction on the next task.

## Rules
- **Do not implement beyond the active task's scope.** If you notice something necessary that isn't in the task, create a new task and report it to the user.
- For brownfield: before modifying an existing file, read it in full and record in the task notes what you found.
- If you hit a blocker (external dependency, technical ambiguity), stop and report immediately. Do not silently invent a solution. If the ambiguity is conceptual, invoke **GRILL** (`references/grill.md`).
- If implementation reveals a new domain term or refines an existing one, update `.spec/CONTEXT.md` via `references/context.md` before continuing.
- If implementation forces a hard-to-reverse decision that wasn't in the plan, create a **doc** via `references/doc.md` and link it from the task notes.
- After each task is done, verify the completion criteria before marking it done.
