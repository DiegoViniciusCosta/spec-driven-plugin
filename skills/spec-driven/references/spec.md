# Phase 1 — SPEC

Before planning anything, understand the problem completely.

## What to do
1. Read the user's request carefully.
2. Ask **at most 3 clarifying questions** if anything is ambiguous. Prefer multiple-choice questions.
3. Pick the next feature number `NNN` by checking existing folders under `.spec/` (start at `001` if empty).
4. Create the feature folder `.spec/NNN-descriptive-slug/` and write the spec to `.spec/NNN-descriptive-slug/spec.md` using the format below.
5. Wait for approval before continuing.

## Spec format

```
## SPEC: [Feature or Change Name]

### Type
[ ] New feature (greenfield)
[ ] Change to existing code (brownfield)
[ ] Bug fix
[ ] Refactoring

### Context
[Briefly describe the current situation — what exists today and what the problem or opportunity is.]

### Goal
[What should be true when this spec is done? Use outcome language, not implementation language.]

### Expected behavior
- [Behavior 1]
- [Behavior 2]
- ...

### Out of scope
- [What this delivery will explicitly NOT do]

### Impact on existing code
- Affected files/modules: [list, or write "none identified yet"]
- Regression risk: Low / Medium / High
- Reason: [brief justification]

### Acceptance criteria
- [ ] [Verifiable criterion 1]
- [ ] [Verifiable criterion 2]
- [ ] [Verifiable criterion 3]
```

## Rules
- Do not invent requirements. If it wasn't stated, ask or put it under "Out of scope".
- For brownfield: always identify the impact on existing code before proceeding.
- If 3 questions are clearly not enough — the task is complex, terms are fuzzy, or boundaries are unclear — propose invoking **GRILL** (`references/grill.md`) instead of stretching the spec phase.
- When a domain term appears that isn't (or conflicts with) `.spec/CONTEXT.md`, update the glossary via `references/context.md` before finalising the spec.
- Only advance after the user confirms: "spec approved" or equivalent.
