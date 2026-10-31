---
name: "tech-stack-protocol"
description: "Phased tech stack for the final product, chosen from an approved system design. Use after into-system-synthesis hands off, or when a system design is in context and the user wants technology chosen."
---

# Tech stack protocol

Turn the approved system design and the crossfire answers in context into the tech stack of the final product, split into at most 3 phases with the MVP as phase 1. Agree it with the user, then hand it to low-level-design-protocol. The stack lives in the conversation.

## 1. Fix the phases

Read the design and the crossfire Q&A in context. If no approved design is there, fire into-system-synthesis first.

Ask the user what must ship in the MVP and what can wait. Fire crossfire-protocol for this, covering only what the context leaves unanswered.

Cut the design into 1 to 3 phases. Phase 1 is the MVP: the smallest set of components that serves the core user journeys end to end. Later phases add components and capacity.

Phase 1 always carries auth and observability, since both are cheap early and painful to retrofit. When the design lacks either component, add it to phase 1 and mark it as yours.

Done when every component in the design sits in exactly one phase, every core journey the user named for the MVP runs on phase 1 components alone, and phase 1 holds auth and observability.

## 2. Draft the stack

Pick one product for each component and boundary in the design, for the final product. Cover the layers the design has a component for: language and framework, data stores, hosting and deployment, auth, messaging, observability, CI, and every third-party service the design names.

Every pick is a final-stack product. Phase 1 uses a subset of them and later phases add the rest, so no phase replaces what an earlier phase shipped.

Each pick carries five lines:

- The product
- The phase it enters
- The component or crossfire answer that drove it
- The strongest rejected alternative and why it lost
- The cost it brings (lock-in, ops burden, learning curve)

Choose against the user's stated constraints: team skills, timeline, scale, compliance, existing systems. Choose _boring_ technology unless an answer demands otherwise, and use fewer products over more. Look up current version and maintenance status for each pick, since memory goes stale.

Name products and technologies. Vendors, tiers, and pricing belong to low-level-design-protocol, which selects a vendor for each service in the stack. Raise budget only when a pick turns on it (a managed service versus self-hosting, say).

Done when every component and boundary has a pick traced to an answer, every pick carries a phase, and every crossfire constraint shapes at least one pick or is listed as not affecting the stack.

When a pick turns on a fact no answer supplies (team skills, hosting preference, compliance), fire crossfire-protocol on that gap, then resume. Whatever you still assume goes under assumptions, marked as yours.

## 3. Agree

Present the stack grouped by phase, MVP first, then ask exactly: "Is any change needed, or does this stack serve your project well?"

When the user asks for changes, apply every one and recheck what each touches (a new database moves the ORM, the hosting, the backup plan, and possibly the phase split). Show the revised stack with the changes marked, then ask exactly: "Is it okay or not?" Repeat this round until the user approves.

A yes with a caveat, or "mostly", is a change request.

When a requested change carries a real downside, state it once with the alternative you would pick. The user's reply settles it: a new reason reopens the pick, a plain reaffirmation keeps the user's choice and the downside moves to risks.

A change that contradicts a crossfire answer goes back to the user as a conflict to settle. A change the design cannot support means the design needs revising: say so and fire into-system-synthesis.

Done when the user's latest message is an explicit yes to the latest version and no objection of yours is still open.

## 4. Hand off

Fire low-level-design-protocol, passing the approved stack in full, with its phases, along with the design.
