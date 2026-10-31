---
name: "low-level-design-protocol"
description: "Low-level design and vendor selection after tech-stack-protocol. Fired by tech-stack-protocol, or use when an approved system design and a chosen tech stack are in context and the user wants component-level design or service vendors."
---

# Low-level design protocol

Turn the system design and tech stack in context into a low-level design with one vendor chosen per service need, agree it with the user, then leave it in context for handoff-architecture-protocol.

## 1. Gather context

Read the crossfire Q&A, the approved system design, and the tech stack decisions in context. When one is missing, fire its skill first: crossfire-protocol, into-system-synthesis, tech-stack-protocol, in that order.

Done when all three are in context.

When a decision needs a fact no answer supplies, or two answers conflict, fire crossfire-protocol on that gap, then resume. Whatever you still assume goes under assumptions, marked as yours.

## 2. Design the low level

Give every component in the system design an entry holding:

- Interfaces: endpoints or events, each with request, response, and error shapes
- Data: tables or collections for the entities it owns, with keys, indexes, and constraints
- Behavior: the sequence for each main journey through it, including failure and retry paths
- Runtime: deployment unit, config, secrets, auth checks
- Observability: the logs, metrics, and alerts that show it has broken

Write each entry in the idioms of the chosen stack.

Done when every component and every main journey from the system design has an entry, and every interface names the entities it reads and writes.

## 3. Choose vendors by tier

Derive the service needs from the design (hosting, database, auth, email, payments, queue, storage, monitoring, and whatever else the components call for). For each need, offer one vendor per tier:

- **Starter**: free or cheapest that works at launch, accepting low limits and manual work
- **Growth**: paid managed service sized for real users
- **Scale**: SLA, compliance certifications, support contract, high limits

Each option states the vendor, its monthly cost at the project's expected usage, the limit that forces the next tier, and the cost of leaving.

Search the vendor's own pages for current pricing and limits before stating them, cite each page, and date the figures. Check that every vendor supports the chosen stack's language and framework.

Set a project tier from the crossfire answers on budget, expected users, and compliance. Pick that tier for each need. Where a need warrants a different tier, say why, citing the answer behind it.

Done when every need has three cited options and one pick whose reason cites a crossfire answer. Run the arithmetic for the monthly total of the picked mix and of each tier taken whole.

## 4. Agree

Present the low-level design, the vendor table with picks, and the monthly totals. Then ask exactly: "Is any change needed, or does it serve your project well?"

When the user asks for changes, apply them and check what else they touch. A vendor swap can change interfaces, and an interface change can change the vendor. Show the revised design with the changes marked, then ask exactly: "Is it okay or not?" Repeat this round until the user approves.

A yes with a caveat, or "mostly", is a change request. A change that contradicts an earlier crossfire answer goes back to the user as a conflict to settle, with crossfire-protocol available for it.

Done when the user's latest message is an explicit yes to the latest version.

## 5. Exit or create

Restate the approved version once, under the heading "Approved low-level design": the component entries, the vendor picks with tier and reason, the monthly totals, and the assumptions.

Then ask exactly: "Exit, or create the artifacts (system design file, tech stack with low-level design file, one HTML file combining both)? Reply with one word: exit or create."

Any reply other than a clear "exit" or "create", such as a partial selection or "maybe", gets the same question again.

- **create:** fire handoff-architecture-protocol, passing everything in context in full: every question and answer from the first crossfire-protocol run onward, the gap-fill rounds, the approved system design, the tech stack decisions, and the approved low-level design.
- **exit:** end the skill with all of that left in the conversation. The user fires handoff-architecture-protocol later.

Done when the user has replied "exit" or "create" and the matching branch has run.
