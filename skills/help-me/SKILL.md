---
name: "help-me"
description: "Explains the genesis protocol flow and where the user is in it. Use when the user types help-me, asks how the genesis flow works, what the stages are, where they are in the protocol, or what comes next."
---

# Help me

Show the user how the genesis protocol works and where they are in it. Answer from the conversation; do not start, advance, or redo any stage.

## 1. Find the current stage

Read the conversation and mark each stage as done, in progress, or not started. A stage is done only when the user approved its output.

1. genesis-the-protocol: the idea is captured in the user's words.
2. crossfire-protocol: done when the user confirmed a shared understanding.
3. into-system-synthesis: done when the user agreed the system design.
4. tech-stack-protocol: done when the user agreed the phased stack.
5. low-level-design-protocol: done when the user agreed the design and vendors, and replied exit or create.
6. handoff-architecture-protocol: done when the three files are written.

When nothing has run yet, the current stage is the start: no project idea is in context.

Done when every stage has a status you can justify from the conversation.

## 2. Explain the flow

Give the user, in plain language:

- One line per stage: what it does and what it produces.
- Which stage they are at, and what has been settled so far.
- The one thing they should do next, using the real phrase the protocol expects: "continue" after crossfire to start the system design, "create" or "exit" at the end of the low-level design.
- That they can describe a change at any approval point to reopen that stage, and that help-me works at any time.

Keep it short enough to read in a minute. Use a numbered list for the stages only if the user is at the start; otherwise lead with where they are.

Done when the user knows what each stage does, where they stand, and what to do next.

## 3. Stop

Do not fire another skill. Wait for the user's next message.
