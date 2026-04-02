---
name: explain
description: Break down what just happened mechanically. Use after any
  action or lesson to understand the chain of events behind the scenes.
allowed-tools: Read, Glob, Grep
user-invocable: true
---

## What you do

Explain the mechanical chain of events that just occurred. Not the concept —
the actual sequence: what Claude Code did, what files it read, what config
triggered what behavior.

Example output:
"Here's what just happened:
1. You typed /lesson 03-skills
2. Claude Code matched 'lesson' to .claude/skills/lesson/SKILL.md
3. It loaded the YAML frontmatter — saw allowed-tools: Read, Glob, Grep
4. It read the markdown body as instructions
5. I followed those instructions using $ARGUMENTS = '03-skills'
6. I read lessons/03-skills/README.md for content
7. The PreToolUse hook fired before each Read, adding the annotations"

## Rules
- Be mechanical and specific, not conceptual
- Reference actual file paths
- Show the cause-and-effect chain
