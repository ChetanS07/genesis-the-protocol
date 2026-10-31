# genesis-the-protocol

A Claude plugin that takes a new project idea from "where do I begin?" to a set of architecture files you can build from. You describe the idea, Claude interviews you until the requirements are settled, and each later stage turns the previous one into something concrete: a system design, a tech stack, a low-level design with vendors, and finally the files.

Every stage ends with your approval. Nothing moves on until you say so, and you can reopen an earlier stage at any point by describing the change you want.

## Install

In Claude Code:

```bash
claude plugin marketplace add ChetanS07/genesis-protocol
claude plugin install genesis-the-protocol@chetan-protocols
```

Replace `ChetanS07/genesis-protocol` with the actual repository path if it differs.

To try it from a local clone instead:

```bash
claude plugin marketplace add ./genesis-protocol
claude plugin install genesis-the-protocol@chetan-protocols
```

## Use it

Start a session and run the entry skill:

```
/genesis-the-protocol:genesis-the-protocol
```

Give it your project idea in your own words. If you don't have one yet, it will ask what you are building. At any point, run `/genesis-the-protocol:help-me` to see the stages, where you are, and what to do next.

## The pipeline

1. `genesis-the-protocol` takes the idea and hands it to crossfire.
2. `crossfire-protocol` interviews you in rounds. Each round asks every question that can be asked without guessing at earlier answers, with a recommended answer for each, and waits for your replies. It ends when you confirm a shared understanding.
3. `into-system-synthesis` turns the answers into a system design and loops with you until you approve it.
4. `tech-stack-protocol` picks a tech stack in at most three phases, with the MVP as phase one, and agrees it with you.
5. `low-level-design-protocol` designs the components and picks one vendor per service need. It can go back to crossfire to fill gaps. You finish by replying `exit` or `create`.
6. `handoff-architecture-protocol` runs when you reply `create`. It writes three files for a reader who never saw the conversation:
   - `system-design.md`
   - `tech-stack-and-low-level-design.md`
   - `architecture-overview.html`

`help-me` sits outside the chain and works at any stage.

Each skill can also be used alone if what it needs is already in the conversation. For example, you can run `tech-stack-protocol` directly when you already have an approved system design.

## Where the files go

In Claude Code, the handoff writes into a `genesis-protocol-docs/` folder at the project root (the git root, or the working directory when there is no repository). The folder is created if it doesn't exist. In apps that can send files, the three files are delivered in the conversation.

## Repository layout

```
.claude-plugin/marketplace.json
plugins/genesis-the-protocol/
├── .claude-plugin/plugin.json
├── README.md
└── skills/
    ├── genesis-the-protocol/
    ├── crossfire-protocol/
    ├── into-system-synthesis/
    ├── tech-stack-protocol/
    ├── low-level-design-protocol/
    ├── handoff-architecture-protocol/
    └── help-me/
```

## Updating

Bump `version` in `plugins/genesis-the-protocol/.claude-plugin/plugin.json` with every change you publish, so installed copies pick up the update.

## License

See the `LICENSE` file.
