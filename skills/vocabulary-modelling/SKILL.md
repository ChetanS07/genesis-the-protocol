---
name: vocabulary-modelling
description: Actively build and sharpen the project's domain model while designing. Challenge terms against vocabulary.md, sharpen fuzzy language, stress-test relationships with scenarios, and write terms down as they resolve. Use when a session is changing the model (new terms, renamed concepts, shifting boundaries); reading vocabulary.md for definitions needs no skill.
---

Build the project's domain model out loud, with the user, and keep `vocabulary.md` current as it takes shape. This is a live discipline, so run it for the whole session, not once at the end.

`vocabulary.md` lives at `./genesis-protocol-docs/vocabulary.md`. It is a glossary and nothing else: no implementation details, no specs, no scratch notes, no decisions. Entry format and rules are in [vocabulary-format.md](vocabulary-format.md). Read it before the first write.

## Challenge

Compare every term the user uses against `vocabulary.md`. On a conflict, say so immediately and ask which meaning holds.

> Your vocabulary defines "cancellation" as X, but you seem to mean Y. Which is it?

## Sharpen

When a term is vague or overloaded, propose one canonical term and ask the user to confirm it.

> You're saying "account". Do you mean the Customer or the User? Those are different things.

## Stress-test

When relationships between concepts come up, invent a concrete scenario that probes an edge case and forces the user to place the boundary. Prefer the case the user hasn't thought of: a Customer who is also a User, an Order split across two Invoices, a cancellation after delivery. Ask about the scenario itself, with names and numbers, so the answer can't stay abstract.

## Record

The moment a term resolves, add or update its entry in `vocabulary.md`, before asking the next question. One entry per resolution, written as it happens. Resolved means the user confirmed the canonical term and its definition. Pick the best word and move the rejected ones under `_Avoid_`.

If `vocabulary.md` doesn't exist yet, create it in `./genesis-protocol-docs/` from the structure in [vocabulary-format.md](vocabulary-format.md).

The session is done when every term the user confirmed is in `vocabulary.md` and no conflict raised during the session is still open.
