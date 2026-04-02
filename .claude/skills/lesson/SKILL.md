---
name: lesson
description: Start a guided lesson on a Claude Code feature.
  Usage: /lesson [topic] where topic matches a lessons/ directory
  (01-CLAUDE-md, 02-settings, 03-skills, 04-hooks, 05-agents, 06-mcp,
  07-putting-it-together). Teaches by pointing at this repo's own
  configuration as a live example.
allowed-tools: Read, Write, Glob, Grep, WebFetch
user-invocable: true
---

## What you do

Teach the requested Claude Code feature following the lesson framework.

1. Read lessons/$ARGUMENTS/README.md for the lesson content.
   If $ARGUMENTS is empty, read .claude-progress.json and suggest
   the next uncompleted lesson.

2. The README contains a mix of literal content and DESIGN INSTRUCTIONS.
   - **Literal content** (USE, APPLY + CHECK): deliver as-is to the learner
   - **[DESIGN INSTRUCTION: ...]** blocks: these are instructions FOR YOU,
     not content for the learner. Read them, then generate the lesson content
     by following the instructions. The learner never sees the brackets.

3. When a DESIGN INSTRUCTION says "FROM DOCS" or references a source URL,
   read the HTML comment at the top of the README to find the SOURCE URL.
   Check .claude-progress.json for the "fetch_docs" preference set during
   /setup.
   - If fetch_docs is true: fetch the page using WebFetch, extract the
     facts listed in the instruction, and weave them into the lesson
     naturally. If the fetch fails, fall back to training knowledge.
   - If fetch_docs is false or missing: use your training knowledge to
     teach the same facts. Add a note at the end: "For the latest
     details, see the Reference link below."
   - The learner chose this during /setup. Don't ask again each lesson.

4. Follow the framework:
   - USE: Use the feature live before explaining it (literal — our design)
   - DEMONSTRATE: Generate from DESIGN INSTRUCTIONS + docs (fetched or
     from training knowledge). Connect facts to this repo's own config files.
   - APPLY + CHECK: Set the task (literal — our design), wait for the
     learner to do it, read their file, give specific pass/fail feedback,
     have them fix issues, verify again, then test it live
   - Gotchas: Generate by merging doc-sourced + experience-based items
   - Tips: Generate by merging doc-sourced + experience-based items

5. After the lesson, update .claude-progress.json:
   add the lesson to "completed", set "current" to null.

## Config-to-lesson mapping
- 01-CLAUDE-md → ./CLAUDE.md
- 02-settings → .claude/settings.json
- 03-skills → .claude/skills/lesson/SKILL.md (this file!)
- 04-hooks → .claude/settings.json hooks section
- 05-agents → .claude/agents/mentor.md or reviewer.md
- 06-mcp → .mcp.json (if it exists)
- 07-putting-it-together → all config files as a system

## APPLY + CHECK pattern
When the lesson says to check the learner's work:
1. Tell them exactly what to create and where
2. Wait for them to say they're done
3. Read the file they created
4. Check each requirement — give ✓ or ✗ with specific feedback
5. If anything fails, give a hint and wait for them to fix it
6. Re-read and verify
7. Once all pass, have them test it live (trigger the feature)

## Rules
- Reference real files in THIS repo, not hypothetical examples
- If a config file doesn't exist (setup wasn't run), tell learner to run /setup
- During APPLY + CHECK, never create the file FOR the learner
- Give hints, not answers, when something is wrong
