# claude-code-learn

**A self-teaching Claude Code tutorial. The repo teaches Claude Code features
by being an example of them.**

Clone it. Read it. Open Claude Code. Type `/setup`.

---

## What this is

7 lessons that teach every major Claude Code feature — CLAUDE.md, settings,
skills, hooks, agents, and MCP — by pointing at this repo's own configuration
as the live example.

The CLAUDE.md IS lesson 01. The skills driving /lesson ARE lesson 03.
The hooks explaining every action ARE lesson 04. You learn each feature by
using it, seeing its config, and building your own.

## How to use it

1. Clone this repo
2. Open it in VS Code with the Claude Code extension (recommended)
   Or: open a terminal and run `claude` from the repo directory
3. Type `/setup` — Claude interviews you and builds your learning environment
   (If setup gets interrupted, just run `/setup` again — it detects and repairs.)
4. Type `/lesson 01-CLAUDE-md` to start

## Before you install

This repo contains only markdown files. No code. No scripts. No executables.

**Audit it yourself:**
- Read `.claude/skills/setup/SKILL.md` — it's the most powerful file (has Write
  permission). It interviews you and creates config files. That's all.
- Or ask Claude: "Read every file in .claude/ and flag anything that accesses
  env vars, runs shell commands, or makes network requests."
- Or scan it: upload the zip to [SkillCheck](https://skills.repello.ai)

See [SECURITY.md](SECURITY.md) for the full security policy and tool permissions.

## Before you start

You need:

1. **[Claude Code](https://code.claude.com)** installed and working (`claude --version` to verify)
2. **One of these** for Claude Code access:

   | Option | Cost | Best for |
   |--------|------|----------|
   | Claude Max subscription | $100-200/mo | Best experience — recommended for learning |
   | Claude Pro subscription | $20/mo | Budget option, may hit usage limits during lessons |
   | Anthropic API key | Pay-per-use | Developers, scripting |
   | OpenRouter | Pay-per-use | Multi-model access, budget flexibility |

   > **Note:** API key and OpenRouter sessions lose context after ~10 minutes
   > of inactivity. For a learning tutorial where you pause to think and read,
   > a Claude subscription gives the best experience.

3. **Git** (to clone this repo)
4. **Node.js 18+** (required for MCP lesson — optional if skipping lesson 06)

**Recommended:** VS Code with the [Claude Code extension](https://marketplace.visualstudio.com/items?itemName=anthropics.claude-code) — chat panel on the right, editor on the left. But any of these work:
- VS Code integrated terminal (`claude` in the terminal pane)
- JetBrains IDEs with Claude plugin
- Windsurf or Cursor
- Terminal only (`claude` CLI, no IDE needed)

## Available commands

| Command | What it does |
|---------|-------------|
| `/setup` | Interview + build your learning environment |
| `/lesson [topic]` | Guided lesson (e.g., /lesson 01-CLAUDE-md) |
| `/explain` | Break down what just happened |
| `/challenge` | Harder hands-on task |
| `/progress` | Show your learning path |
| `/UDA [topic]` | Full Use → Demonstrate → Apply loop |

## Philosophy

Built on principles from [FrontierBoard](https://github.com/stefans71/FrontierBoard)
and [NanoClaw](https://github.com/qwibitai/NanoClaw):

> Small enough to understand. AI-native. Claude Code is the installer,
> the runtime, and the operator.

No installation scripts. No configuration sprawl. No code that runs before
you trust it. Just Claude reading markdown and building from your answers.

## License

MIT
