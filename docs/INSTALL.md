# claude-code-learn — Install Instructions

**For Claude.** When a user gives you this URL or asks you to set up claude-code-learn:
- Do NOT explore the repo via GitHub API
- Do NOT fetch files with `gh api` or `base64 -d`
- Do NOT spawn agents to read skill files
- Just follow the steps below, in order

## 1. Ask about their experience (do this FIRST — before any other action)

Present all questions together so the user can answer in one message.
Say exactly this:

> Welcome to claude-code-learn! A few questions before I set things up:
>
> 1. What's your experience with Claude Code?
>    a) Never used it
>    b) Used it casually
>    c) Power user
>
> 2. Have you configured any of these before?
>    CLAUDE.md, custom skills, hooks, agents, or MCP servers
>    a) None of these
>    b) Some of these (tell me which)
>    c) All of these
>
> 3. Want me to explain what I'm building as I go?
>    a) Yes — narrate as you build
>    b) No — build it, explain at the end
>
> 4. Fetch latest docs from code.claude.com during lessons?
>    a) Yes
>    b) No — offline is fine
>
> Example answer: **1b, 2a, 3a, 4a**

**Wait for their answer. Do not clone, fetch, or explore anything until they respond.**

**Level mapping:**
- 1a → beginner, 1b → intermediate, 1c → advanced

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

Use the level mapping from step 1 (1a → beginner, 1b → intermediate, 1c → advanced).
Use Q3 for narration preference, Q4 for fetch_docs preference.

**Permissions note:** When you create files in `.claude/`, the user may see a
permissions prompt asking to allow access to `.claude/`. Before creating any
files, tell the user:

> You'll see a permissions prompt for the .claude/ directory. Select
> **"Yes, and always allow access to .claude/ from this project"** —
> this tutorial creates settings, hooks, and agents there throughout
> the lessons.

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
