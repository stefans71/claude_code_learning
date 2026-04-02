# claude-code-learn — Install Instructions

**For Claude.** When a user gives you this URL or asks you to set up claude-code-learn:
- Do NOT explore the repo via GitHub API
- Do NOT fetch files with `gh api` or `base64 -d`
- Do NOT spawn agents to read skill files
- Just follow the steps below, in order

## 1. Lesson picker (do this FIRST — before any other action)

**Present as a wizard-style Q&A. Use Claude Code's multi-step input format
so the user gets an interactive form experience.**

**The lesson picker IS the assessment.** No separate experience questions.

```
Welcome to claude-code-learn! 7 lessons, starting with 4 fundamentals.

Which basics do you want to skip?

a) [ ] 01-CLAUDE-md — project instructions that shape Claude's behavior
b) [ ] 02-settings — permissions, model config, settings.json
c) [ ] 03-skills — slash commands you can build yourself
d) [ ] 04-hooks — automated actions on every edit

Type letters to skip (e.g. "a c" marks them [X]),
or "all" to skip all basics, or "none" to keep them all.
```

**Wait for their answer. Do not clone, fetch, or explore anything until they respond.**

Then ask one follow-up:

```
Fetch latest docs from code.claude.com during lessons?

a) Yes
b) No — offline is fine
```

**Level mapping (derived from skips):**
- Skipped 0 → beginner, Skipped 1-3 → intermediate, Skipped all → advanced

## 2. Clone the repo (one command)

Clone into the user's current working directory or a sensible default:

```bash
git clone https://github.com/stefans71/claude_code_learning.git
```

Then `cd` into the clone:

```bash
cd claude_code_learning
```

## 3. Read CLAUDE.md and run setup from their answers

Read `CLAUDE.md` from the clone you just created (not from GitHub).

Then create the learning environment using the answers from step 1. Follow the setup skill instructions at `.claude/skills/setup/SKILL.md` — but **skip the interview** since you already asked in step 1. Jump straight to the "What you build" section.

Use the level mapping from step 1:
- Skipped 0 basics → beginner (narrate everything)
- Skipped 1-3 → intermediate (narrate builds, lighter explanations)
- Skipped all 4 → advanced (build quietly, minimal explanation)

**Permissions note:** The repo ships with `.claude/settings.json` containing
pre-approved write permissions for setup paths. File writes should NOT prompt
the user. If a permissions prompt does appear, tell the user to select
"Yes, and always allow access to .claude/ from this project."

**IMPORTANT:** The repo's `.claude/settings.json` already has a `permissions`
block. When adding hooks, **merge into the existing file** — do NOT overwrite
the permissions. Read the file first, then write back with both `permissions`
and `hooks` keys.

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
