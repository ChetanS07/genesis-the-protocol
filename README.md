# genesis-the-protocol

A Claude plugin that takes a new project idea from "where do I begin?" to a set of architecture files you can build from. You describe the idea, Claude interviews you until the requirements are settled, and each later stage turns the previous one into something concrete: a system design, a tech stack, a low-level design with vendors, and finally the files.

Every stage ends with your approval. Nothing moves on until you say so, and you can reopen an earlier stage at any point by describing the change you want.

## Install

In Claude Code:

```bash
claude plugin install genesis-the-protocol@cs-genesis
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

## License

See the `LICENSE` file.
