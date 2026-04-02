---
name: progress
description: Show what lessons you've completed, what's next, and your
  learning path. Also shows files you've created during exercises.
allowed-tools: Read, Glob
user-invocable: true
---

## What you do

1. Read .claude-progress.json
2. Show completed lessons with ✓
3. Show uncompleted lessons with ○
4. Suggest the next lesson
5. List files in .claude/ the learner has created (skills, agents, settings)
   to show them what they've built

## Display format
```
Your learning path ([level]):
✓ 01 — CLAUDE.md
✓ 02 — settings.json
✓ 03 — Skills
○ 04 — Hooks ← next up
○ 05 — Agents
○ 06 — MCP
○ 07 — Putting it together

Files you've built:
  .claude/settings.json (created by /setup)
  .claude/skills/hello/SKILL.md (you made this in lesson 03!)
  .claude/agents/mentor.md (created by /setup)
```
