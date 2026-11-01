---
name: help-me
description: Explains how the genesis plugin works, which skills run in what order, and what you do at each step.
disable-model-invocation: true
---

# Help me

Answer the user's question about the genesis plugin from the reference below. Lead with the answer. When the question is open ("how does this work?"), walk the flow in order.

Done when the user's question is answered and they know what to do next.

## The flow

genesis-the-protocol, then crossfire-protocol, then into-system-synthesis, then tech-stack-protocol, then low-level-design-protocol, then handoff-architecture-protocol.

Every skill except help-me can be fired by the agent, and you can type any of them by name to start or resume at that point. Each skill fires the one before it when its input is missing from the conversation.

| Skill | Started by | Job | Ends when |
| --- | --- | --- | --- |
| genesis-the-protocol | you or the agent | Takes your project idea and fires crossfire-protocol and vocabulary-modelling together | Crossfire ends and `vocabulary.md` holds your confirmed terms |
| crossfire-protocol | genesis, any later skill with a gap, or the agent | Interviews you in rounds until you and the agent share one understanding | You confirm the understanding |
| into-system-synthesis | the agent after crossfire, or you | Builds a system design from the crossfire answers | You say an explicit yes to the latest design |
| tech-stack-protocol | into-system-synthesis, or you | Picks one product per component, split into at most 3 phases with the MVP first | You say an explicit yes to the latest stack |
| low-level-design-protocol | tech-stack-protocol, or you | Designs each component in detail and offers three vendors per service need (Starter, Growth, Scale) with cited, dated prices | You approve, then reply "exit" or "create" |
| handoff-architecture-protocol | low-level-design-protocol on "create", or you | Writes the approved work into three files | You can open all three |
| help-me | you only | This reference | Your question is answered |

## Starting

Type genesis-the-protocol followed by a sentence about what you are building. Without the sentence, it asks "What are you building?" first.

Genesis fires crossfire-protocol and vocabulary-modelling together. Crossfire interviews you in rounds. Vocabulary-modelling runs alongside it, flags terms that conflict with `vocabulary.md` or sound vague, and records each term in `vocabulary.md` once you confirm it. Its questions arrive inside crossfire's rounds, so you answer one numbered set at a time. A "yes" accepts the recommended answer under a question. The interview ends when you confirm that you and the agent share one understanding.

## Moving to the system design

After you confirm in crossfire, genesis says that into-system-synthesis is next. Reply "continue", or type into-system-synthesis yourself. It builds the system design from your crossfire answers and asks "Is any change needed, or does it serve your project well?" until you approve.

The same approval rule holds at every agree step in the flow: a yes with a caveat, or "mostly", counts as a change request and starts another round.

## After the low-level design

Once you approve the low-level design and its vendor picks, the agent restates the approved version under the heading "Approved low-level design", with the component entries, vendor picks, monthly totals, and assumptions. It then asks you to reply with one word:

- **create**: it fires handoff-architecture-protocol, which writes the three files from everything in the conversation.
- **exit**: the skill ends and everything stays in the conversation. Type handoff-architecture-protocol later to write the files.

Any other reply, such as "maybe", gets the same question again.

## What you get

Three files: `system-design.md`, `tech-stack-and-low-level-design.md`, and `architecture-overview.html`.

- In Claude Code they land in `genesis-protocol-docs/` at the project root.
- In chat they arrive as attachments.

Any detail the session never settled is written as "Not decided in this session", so a reader sees the gap.

## Good to know

- Everything lives in the conversation. A new conversation starts without the design, so write the files before closing one you want to keep.
- A skill started mid-flow looks in the conversation for the earlier outputs it needs. When one is missing, it fires the skill that produces it, in flow order, or fires crossfire-protocol when the gap is a single fact.
- A change late in the flow can reopen an earlier decision. The agent sends it back to the skill that owns it for re-approval, then resumes.
