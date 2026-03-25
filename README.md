# Agent Kernel

The easiest way to create an AI agent. Clone, start, talk.

Your agent remembers between sessions, takes notes, and builds on past work. No framework, no database — just three markdown files and a git repo.

Works with any AI coding agent: OpenCode, Claude Code, Codex, Cursor, Windsurf, etc.

> 🚀 **[kern-ai](https://github.com/oguzbilgic/kern-ai)** — a runtime built for agent-kernel. Daemon mode, Telegram, Slack, and one brain across every channel. `npx kern-ai init my-agent`

## Quick start

**With any coding agent:**

```bash
git clone https://github.com/oguzbilgic/agent-kernel.git my-agent
cd my-agent
opencode     # or claude, codex, cursor, etc.
```

**With [kern-ai](https://github.com/oguzbilgic/kern-ai) (daemon + Telegram + Slack):**

```bash
npx kern-ai init my-agent
npx kern-ai tui
```

That's it. The agent reads the kernel, realizes it's new, asks who you want it to be. You tell it. It remembers.

## Memory structure

```
AGENTS.md          ← kernel (generic, don't edit)
IDENTITY.md        ← who this agent is (agent maintains)
KNOWLEDGE.md       ← index of knowledge files (agent maintains)
knowledge/         ← facts about the world (mutable)
notes/             ← daily session logs (append-only)
```

Two kinds of memory:

- **`knowledge/`** — State. Facts about how things are right now. The agent updates these when reality changes.
- **`notes/`** — Narrative. What happened each session — decisions, actions, open items. Append-only. Never modified after the day ends.

## Why this works

AI agents already read `AGENTS.md` (or `CLAUDE.md`, `.cursorrules`, etc.) as project instructions. This kernel uses that mechanism to teach the agent *how to remember*.

The agent doesn't need a database, a vector store, or a custom framework. It just needs:
- A file that says "you are stateful, here's how"
- A git repo to store memory in
- Plain markdown files

## Multiple agents

Each agent is its own repo. To create another:

```bash
git clone https://github.com/oguzbilgic/agent-kernel.git another-agent
cd another-agent
opencode     # or claude, codex, etc.
```

Same kernel, different identity, different knowledge. You can have a homelab agent, an investing agent, a health agent — all running the same OS.

## License

MIT
