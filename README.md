# spec-driven (Cursor plugin)

> ⚠️ **Work in progress — not yet published to the Cursor marketplace.** APIs, command names, and file layout may change. Use at your own risk and pin to a commit if you depend on it.

A disciplined four-phase workflow for software changes: **Spec → Plan → Create Tasks → Execute**. Each phase is gated by explicit approval, and three cross-cutting tools keep clarity, vocabulary, and decisions under control.

## What you get

**Phases (sequential, gated by user approval)**

| Command | Phase | Produces |
|---------|-------|----------|
| `/spec <description>` | 1. Understand the problem | `.spec/NNN-slug/spec.md` |
| `/plan <NNN-slug>` | 2. Design the approach | `.spec/NNN-slug/plan.md` |
| `/tasks <NNN-slug>` | 3. Break into atomic tasks | `.spec/NNN-slug/tasks/TASK-*.md` |
| `/execute <NNN-slug> <TASK-NNN>` | 4. Implement one task | code + `[x] Done` |

**Cross-cutting tools (invokable anytime, independently)**

| Command | Tool | Produces |
|---------|------|----------|
| `/grill <topic>` | Clarifying interview | clarity (and possibly context/doc updates) |
| `/context <term>` | Update domain glossary | entries in `.spec/CONTEXT.md` |
| `/doc <decision>` | Record a hard-to-reverse decision | `.spec/docs/NNNN-*.md` |

## Why phase isolation matters

Every command runs in **its own session**. Each one ends by telling you the exact next command to run and refuses to advance further. The `.spec/` folder is the shared memory between sessions — phases read from artifacts, not from chat history. This keeps context windows clean and forces decisions to land in files rather than fade into transcripts.

## Workspace layout

The plugin writes everything to `.spec/` at your project root:

```
.spec/
  CONTEXT.md                       ← shared domain glossary (created lazily)
  docs/                            ← shared decision records (created lazily)
    0001-event-sourced-orders.md
  001-user-registration/
    spec.md
    plan.md
    grill.md                       ← (optional) grilling session log
    tasks/
      TASK-001-create-users-table.md
      TASK-002-expose-post-users.md
```

`.spec/` is meant to be committed — specs, plans, glossary, and docs become part of your project's history and are reviewable in PRs.

## Installation

### Local development

```bash
# Copy or symlink this folder into Cursor's local plugin directory
ln -s /path/to/cursor-plugin ~/.cursor/plugins/local/spec-driven
```

Then restart Cursor (or run "Developer: Reload Window").

### From the marketplace

Not available yet — the plugin is still in development and has not been submitted to the Cursor marketplace.

## Typical flow

```
/spec "add shopping cart with 30-day expiration"
   → Spec saved at .spec/004-shopping-cart/spec.md
   → (new session)
/plan 004-shopping-cart
   → Plan saved
   → (new session)
/tasks 004-shopping-cart
   → 5 tasks created
   → (new session per task)
/execute 004-shopping-cart TASK-001
   → TASK-001 done and verified
   → (new session)
/execute 004-shopping-cart TASK-002
   ...
```

Need clarity at any point? Invoke `/grill <what's unclear>`. Need to capture a domain term? `/context <term>`. Need to record a hard-to-reverse decision? `/doc <decision>`.

## License

MIT
