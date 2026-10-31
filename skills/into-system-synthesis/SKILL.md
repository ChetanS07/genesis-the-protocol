---
name: "into-system-synthesis"
description: "System design from crossfire-protocol answers. Use after crossfire-protocol finishes, or when requirements are already gathered and the user wants a system design."
---

# Into system synthesis

Turn the crossfire-protocol questions and answers in context into a system design, agree it with the user, then hand it to tech-stack-protocol. The design lives in the conversation.

## 1. Draft the design

Read the crossfire Q&A in context. If none is there, fire crossfire-protocol first.

Build the design from the answers. It holds:

- Components, each with one responsibility
- Data flow between components for the main user journeys
- Core data entities and which component owns each
- External boundaries: users, third-party systems, integrations
- Key decisions, each citing the crossfire answer that drove it
- Risks and assumptions

Name components by role ("job queue", "auth service"). tech-stack-protocol chooses the products.

Done when every crossfire answer appears in the design or is listed as deliberately left out with a reason, and every component traces to an answer.

When the design needs a fact no answer supplies, or two answers conflict, fire crossfire-protocol on that gap, then resume. Whatever you still assume goes under assumptions, marked as yours.

## 2. Agree

Present the design, then ask exactly: "Is any change needed, or does it serve your project well?"

When the user asks for changes, apply them and check what else they touch. Show the revised design with the changes marked, then ask exactly: "Is it okay or not?" Repeat this round until the user approves.

A yes with a caveat, or "mostly", is a change request. A change that contradicts an earlier crossfire answer goes back to the user as a conflict to settle, with crossfire-protocol available for it.

Done when the user's latest message is an explicit yes to the latest version.

## 3. Hand off

Fire tech-stack-protocol, passing the approved design in full.