---
name: "genesis-the-protocol"
description: Entry to the genesis protocol. Use when the user wants to design, architect, or plan a new project or product from scratch, or names a project idea and asks where to begin.
---

# Genesis, the protocol

The entry point of the plugin. Take the user's project idea, run crossfire-protocol on it until the user confirms a shared understanding, then point the user to the next skill.

## 1. Take the idea

Read the user's message for the project. Carry their words forward unedited.

When the message names no project, ask one question, "What are you building?", and wait for the answer.

When the conversation already holds a crossfire Q&A that the user confirmed, go to step 3.

Done when the project idea sits in context in the user's own words.

## 2. Fire crossfire

Fire crossfire-protocol with the idea. Crossfire runs the rounds, finds the facts, and asks for the confirmation, so genesis adds nothing to the interview.

Done when crossfire-protocol has ended on the user's explicit confirmation of shared understanding.

## 3. Hand to the user

Say:

"Requirements are settled. Next is into-system-synthesis, which turns them into a system design. Say continue to start it. Type help-me any time to see how the whole flow works."

Done when the user has seen the next step and the help-me command.
