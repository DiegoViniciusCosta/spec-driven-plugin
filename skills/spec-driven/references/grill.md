# GRILL — clarifying interview (cross-cutting tool)

A focused interview that surfaces ambiguity by stress-testing what the user just said against the project's existing language, code, and concrete scenarios.

**Not a phase.** Invokable at any point — during SPEC, PLAN, CREATE TASKS, or EXECUTE — whenever clarity is missing.

## When to use

Invoke GRILL when any of these are true:
- The task touches multiple concepts and their boundaries are fuzzy.
- The user's terms might conflict with what is in `.spec/CONTEXT.md`.
- A decision is "hard to reverse" — a wrong assumption now is expensive later.
- You (or the user) cannot describe the happy path and 2 edge cases without hesitation.

When the topic is small, well-bounded, or already obvious: **skip GRILL**.

## How it works

1. Interview the user **one question at a time**. Wait for the answer before asking the next.
2. For each question, **propose your recommended answer** — don't just ask open-ended.
3. If a question can be answered by reading the code, **read the code instead of asking**.
4. As clarity crystallises, route the outputs to the right tool:
   - New or refined domain terms → update `.spec/CONTEXT.md` via `references/context.md`.
   - Hard-to-reverse decisions → create a doc via `references/doc.md`.

## What to probe

- **Glossary conflicts.** If the user uses a term that contradicts `.spec/CONTEXT.md`, surface it immediately: "Your glossary defines X as A, but you seem to mean B — which is it?"
- **Fuzzy terms.** Propose a canonical name: "You said 'account' — Customer or User? They're different."
- **Concrete scenarios.** Invent edge cases that force precision about boundaries: "What happens if the order is partially shipped when it's cancelled?"
- **Code vs. intent contradictions.** If the code already disagrees with what the user just stated, surface it: "Your code cancels whole Orders, but you said partial cancellation works — which is right?"

## Optional session log

For long grills, record the session at `.spec/NNN-slug/grill.md` (in the active feature folder) — open questions, answers given, and pointers to context/doc updates. Skip if the session was short and the outputs already capture everything.

## Rules

- One question at a time. Always.
- Always offer a recommended answer with each question.
- Update `.spec/CONTEXT.md` and create docs **inline as decisions crystallise** — don't batch at the end.
- GRILL produces clarity, not a plan. When the user is ready, return to the phase you came from.
