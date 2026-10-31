---
name: "handoff-architecture-protocol"
description: "Handoff of the approved architecture into files. Fired by low-level-design-protocol when the user replies create, or by the user to write the system design file, the tech stack with low-level design file, and one HTML overview from the session context."
---

# Handoff architecture protocol

Turn the approved system design, tech stack, low-level design, and crossfire Q&A in context into three files: `system-design.md`, `tech-stack-and-low-level-design.md`, and `architecture-overview.html`. Write them for a reader who never saw this conversation and has to build from them.

## 1. Gather context

Collect from the conversation:

- every crossfire question and answer, gap-fill rounds included
- the approved system design
- the tech stack decisions
- the section headed "Approved low-level design", with its vendor tables, picks, monthly totals, and assumptions

When one is missing, fire the skill that produces it, in this order: crossfire-protocol, into-system-synthesis, tech-stack-protocol, low-level-design-protocol. A design the user has not approved counts as missing.

Done when all four are in context and each is the latest approved version.

Every statement in the files comes from this context.

## 2. Audit gaps

Every section named in steps 4 and 5 is a slot. Walk the slots one by one and mark each as filled or empty from the context. Treat a slot as empty when the context holds nothing for it, and also when it holds only a vague line such as "standard auth" with no named method.

Group the empty slots into one crossfire round and fire crossfire-protocol on them. Then split the answers by effect:

- An answer that only fills a slot (project name, purpose, a missing source URL) goes straight into the files.
- An answer that changes an approved decision returns to the skill that owns it (into-system-synthesis for the design, tech-stack-protocol for the stack, low-level-design-protocol for components and vendors) for re-approval, then this skill resumes.

A slot the user declines to answer, or leaves open after the round, is written as "Not decided in this session", so the reader sees the gap.

Done when no slot is empty without an explicit user decline, and the latest approved versions are in context.

## 3. Pick the destination

- **Claude Code** (the session has no SendUserFile tool): write into `genesis-protocol-docs/` at the project root. The root is the git root, or the working directory when there is no repo. Create the folder when it is absent.
- **Chat** (SendUserFile is available): write the three files in the working directory and send them in step 8.

When files with these names already exist in the destination, Read them, then replace them. The new run reflects the latest approved design.

Done when the destination is named.

## 4. Write system-design.md

Sections, in order:

1. Project: name, purpose, users, taken from the crossfire answers.
2. Requirements: functional, non-functional, and constraints (budget, expected users, compliance, timeline).
3. Architecture: each component with its responsibility, owned data, and dependencies, plus a Mermaid diagram of components and flows.
4. Journeys: each main journey step by step through the components, failure paths included.
5. Integrations: every external system and what crosses the boundary.
6. Decisions: each with its reason and the crossfire answer behind it.
7. Assumptions and open items.
8. Appendix: the crossfire Q&A in full, in the order asked.

Done when every component, journey, requirement, constraint, integration, and decision in the approved design has a place, and every crossfire question appears with its answer.

## 5. Write tech-stack-and-low-level-design.md

Sections, in order:

1. Tech stack: one row per layer (frontend, backend, data, infrastructure, tooling, and any other layer decided) with the choice, its version when settled, the reason, and the alternatives considered.
2. Low-level design: one entry per component, named exactly as in `system-design.md`, holding interfaces, data, behavior, runtime, and observability as approved.
3. Vendors and pricing: for each service need, a table with Starter, Growth, and Scale options. Each option shows the vendor, monthly cost at expected usage, the limit that forces the next tier, the cost of leaving, the source URL, and the date of the figure. Below the table, the pick with its reason and the crossfire answer behind it.
4. Monthly totals: the picked mix and each tier taken whole, with the arithmetic shown.
5. Assumptions.

Copy figures unchanged from the approved low-level design, and keep the date each was gathered, so the reader can judge how stale it is.

Done when every layer, component, and service need is present, and every price carries its source and date.

## 6. Build architecture-overview.html

Load frontend-design with the Skill tool when it is listed. Build from the two markdown files so the three stay in agreement.

Four sections, in this order, behind a sticky section nav:

1. **About**: one paragraph of three to five sentences on what the project is, who it serves, and what it does.
2. **System design**: an inline SVG of the components and their flows, a component table, and a short line per journey.
3. **Tech stack**: a table of layers, choices, and reasons.
4. **Low-level design and pricing**: one collapsible entry per component, then per service need a tier comparison with the picked option marked, then monthly totals for each tier and for the picked mix.

One self-contained file: inline CSS and JS, no network resources, readable at phone width, light and dark through `prefers-color-scheme`, and clean when printed.

Done when the four sections appear in order and every component name, vendor, price, and total matches the markdown text exactly.

## 7. Check

Run a script that:

- finds every monthly total and vendor name from `tech-stack-and-low-level-design.md` in the HTML
- re-adds the totals from the per-need figures
- finds every component name from `system-design.md` in the other two files

Fix each mismatch at its source, rebuild what depends on it, and run the script again.

Done when the script reports zero mismatches.

## 8. Deliver

- **Claude Code:** state the folder path and the three file paths.
- **Chat:** call SendUserFile with all three files, the markdown files with `display: "attach"` and the HTML with `display: "render"`.

Close with two sentences: what was written and where, and how many "Not decided in this session" gaps the files hold.

Done when the user can open all three files.
