# Security Policy for claude-code-learn

## What this repo contains
Markdown files and JSON templates. Nothing else.

## What this repo does NOT contain
- No executable scripts (.sh, .py, .js, .bat)
- No shell injection (!backtick syntax in skills)
- No references to environment variables in skill instructions
- No network calls without explicit user consent (the /lesson skill may
  fetch documentation from code.claude.com based on the user's choice
  during /setup — stored in .claude-progress.json as fetch_docs)
- No binary files, encoded content, or obfuscated anything
- No dependencies (no package.json, requirements.txt, Dockerfile)

## How to verify

**2-minute human audit:**
Read .claude/skills/setup/SKILL.md. It's the most powerful file in the
repo (it has Write permission). It interviews you and creates markdown/JSON
files. That's everything it does.

**Claude audit:**
Open Claude Code in this repo and ask:
"Read every file in .claude/ and tell me: Does anything reference
environment variables? Run shell commands? Make network requests?
Use !backtick injection? What tool permissions does each skill request?"

**Scanner audit:**
- SkillCheck (skills.repello.ai) — upload the repo zip, 60 seconds
- Cisco skill-scanner — pip install skill-scanner && skill-scan .

## Tool permissions

| Skill | Tools | Why |
|-------|-------|-----|
| /setup | Read, Write, Glob | Creates config files during interview |
| /lesson | Read, Write, Glob, Grep, WebFetch | Reads lessons, writes progress updates. WebFetch optional — respects user preference set during /setup |
| /explain | Read, Glob, Grep | Reads recent actions and config |
| /challenge | Read, Glob, Grep | Reads progress, presents tasks |
| /progress | Read, Glob | Reads progress tracker |
| /UDA | Read, Write, Glob, Grep | Teaches + writes exercise files |

| Agent | Tools | Why |
|-------|-------|-----|
| mentor | Read, Grep, Glob | Read-only. Asks Socratic questions. |
| reviewer | Read, Grep, Glob | Read-only. Checks exercise work. |

## Reporting vulnerabilities
Open an issue or contact the maintainers.
