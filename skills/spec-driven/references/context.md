# CONTEXT — shared domain glossary (cross-cutting tool)

`.spec/CONTEXT.md` is the project's **domain glossary**: a shared, living memory of what each term means across all features.

**Not a phase.** Update it whenever a new domain term shows up or an existing one is refined — during SPEC, GRILL, PLAN, EXECUTE, or while reading code.

## When to update

- A new domain concept appears in conversation or in a spec and isn't in `CONTEXT.md` yet.
- An existing term is being used with a different meaning than what's documented.
- GRILL resolved a fuzzy or overloaded term into a canonical one.
- You discovered, while reading code, that a term has a precise meaning the glossary doesn't capture.

If the term is purely technical (a class name, a library, a pattern), it does **not** belong in `CONTEXT.md`. Glossary entries are about the **domain**.

## Hard rules

`CONTEXT.md` is a glossary and **nothing else**:

- **No implementation details** — no class names, file paths, libraries, frameworks.
- **No decisions** — those go in docs (see `references/doc.md`).
- **No scratch notes, todos, or open questions.**
- **No spec content** — specs live in `.spec/NNN-slug/spec.md`.

If you're tempted to write something that isn't a definition, it doesn't belong here.

## File location

```
.spec/
  CONTEXT.md          ← shared across all features
```

One file at the root of `.spec/`. Do **not** create per-feature `CONTEXT.md` files — the glossary is a single source of truth.

Create the file lazily — only when resolving the first term. Until then, it doesn't need to exist.

## Format

```markdown
# Domain Context

## [Term]
[One-paragraph definition in domain language. What it is, what it is not, how it relates to other terms.]

## [Term]
[Definition...]
```

Keep entries alphabetical for easy scanning. When a term relates to another, link it inline: `An [Order](#order) becomes...`.

## How to update

- Add or edit the entry **inline, the moment the term is resolved.** Don't batch updates.
- If a term changes meaning, update the definition in place — don't keep "old" versions around. Git history is the audit trail.
- If a term is no longer used anywhere, delete it.
- Keep the language the user uses, not your translation of it.
