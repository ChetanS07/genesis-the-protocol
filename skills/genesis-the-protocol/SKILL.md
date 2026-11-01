---
name: genesis-the-protocol
description: Entry to the genesis protocol. Use when the user wants to design, architect, or plan a new project or product from scratch, or names a project idea and asks where to begin.
---

# Genesis, the protocol

The entry point of the plugin. Take the user's project idea, run crossfire-protocol and vocabulary-modelling on it together until the user confirms a shared understanding, then point the user to the next skill.

## 1. Take the idea

Read the user's message for the project. Carry their words forward unedited.

When the message names no project, ask one question, "What are you building?", and wait for the answer.

When the conversation already holds a crossfire Q&A that the user confirmed, go to step 3.

Done when the project idea sits in context in the user's own words.

## 2. Fire crossfire and vocabulary-modelling together

Fire crossfire-protocol and vocabulary-modelling in the same turn, both with the idea. Both stay active until the interview ends.

- crossfire-protocol runs the rounds, finds the facts, and asks for the confirmation.
- vocabulary-modelling watches every term the user uses, and records each resolved term in `vocabulary.md` as it settles.

The user answers one set of questions per round. When vocabulary-modelling has a challenge, a sharpening, or a scenario, it joins crossfire's round as one of its numbered questions.

Done when crossfire-protocol has ended on the user's explicit confirmation of shared understanding and `vocabulary.md` holds every term the user confirmed, with no conflict left open.

## 3. Hand to the user

Say:

"Requirements are settled and the terms are recorded in vocabulary.md. Next is into-system-synthesis, which turns them into a system design. Say continue to start it. Type help-me any time to see how the whole flow works."

Done when the user has seen the next step and the help-me command.
