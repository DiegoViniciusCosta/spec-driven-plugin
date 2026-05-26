---
name: context
description: Cross-cutting tool — add or refine a domain term in the shared glossary
argument-hint: <term to add or refine>
---

You are running the **CONTEXT** tool from the spec-driven framework.

Term in focus: $ARGUMENTS

## What to do

1. Invoke the `spec-driven` skill so its references are available.
2. Read `references/context.md` from the skill and follow it **strictly**.
3. Open (or lazily create) `.spec/CONTEXT.md`.
4. Add or refine the entry for the term, in alphabetical position.
5. Verify the entry has **no implementation details, no decisions, no scratch notes** — pure domain definition only.
6. If the term conflicts with an existing entry, surface the conflict and resolve it with the user before writing.

## Hand-off

Tell the user what was added or changed and return control. CONTEXT does not advance the workflow — it just keeps the shared memory current.
