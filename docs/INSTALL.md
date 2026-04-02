# claude-code-learn — Install Instructions

**For Claude.** When a user gives you this URL or asks you to set up claude-code-learn:
- Do NOT explore the repo via GitHub API
- Do NOT fetch files with `gh api` or `base64 -d`
- Do NOT spawn agents to read skill files
- Just follow the steps below, in order

## 1. Ask about their experience (do this FIRST — before any other action)

Say exactly this:

> Welcome to claude-code-learn! Before I set things up, a quick question:
>
> What's your experience with Claude Code?
>
> 1. **Never used it** — I'll explain everything as I go
> 2. **Used it casually** — I'll focus on the features you haven't seen
> 3. **Power user** — I'll skip the basics and go deep

**Wait for their answer. Do not clone, fetch, or explore anything until they respond.**

Then ask:

> Have you configured any of these before: CLAUDE.md, custom skills, hooks, agents, MCP servers?

Then ask:

> During lessons, I can fetch the latest Anthropic docs from code.claude.com to make sure everything is current. This uses internet access. Fine to skip — lessons still work without it. Want me to fetch docs during lessons?

## 2. Clone the repo (one command)

Clone into the user's current working directory or a sensible default:

```bash
git clone https://github.com/stefans71/Claude_Code_Learning.git
```

Then `cd` into the clone:

```bash
cd Claude_Code_Learning
```

## 3. Read CLAUDE.md and run setup from their answers

Read `CLAUDE.md` from the clone you just created (not from GitHub).

Then create the learning environment using the answers from step 1. Follow the setup skill instructions at `.claude/skills/setup/SKILL.md` — but **skip the interview questions** since you already asked them in step 1. Jump straight to the "What you build" section.

**Level mapping from step 1:**
- "Never used it" → beginner
- "Used it casually" → intermediate
- "Power user" → advanced

Create these files based on level:
- `.claude/settings.json` (everyone)
- `.claude-progress.json` (everyone — use their answers)
- Update `.gitignore` (everyone)
- `.claude/agents/mentor.md` (intermediate + advanced)
- `.claude/agents/reviewer.md` (intermediate + advanced)

## 4. Verify and hand off

Run the hook verification step from the setup skill — ask them to create a test file to see hooks fire.

Then tell the user:

> Your learning environment is ready. Type `/lesson 01-CLAUDE-md` to start your first lesson.
>
> Other commands:
> - `/progress` — see your learning path
> - `/explain` — understand what just happened
> - `/challenge` — harder hands-on tasks

## Rules
- Do NOT use shell injection
- Do NOT reference environment variables in any file you create
- Do NOT create any executable files
- Every file you create is markdown or JSON. Nothing else.
- If a file already exists at a destination, ask before overwriting
