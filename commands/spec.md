---
name: spec
description: Phase 1 — SPEC: understand the problem and write the feature spec
argument-hint: <short description of the feature or change>
---

You are executing **Phase 1 (SPEC)** of the spec-driven framework.

User input: $ARGUMENTS

## What to do

1. Invoke the `spec-driven` skill so its references are available.
2. Read `references/spec.md` from the skill and follow it **strictly**.
3. If terms used in the request are likely to land in `.spec/CONTEXT.md`, skim it first (if it exists) to stay consistent.
4. Ask at most 3 clarifying questions. If you need more, propose `/grill` instead.
5. Pick the next feature number `NNN` by listing existing folders under `.spec/`.
6. Create `.spec/NNN-descriptive-slug/spec.md` with the spec in the required format.
7. Wait for the user to say "spec approved" (or equivalent).

## Hand-off

After approval, tell the user **verbatim**:

> Spec saved at `.spec/NNN-slug/spec.md`. For context isolation, open a fresh session and run `/plan NNN-slug` to continue.

Do **not** continue into PLAN in this session.
