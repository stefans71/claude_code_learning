---
name: UDA
description: Run the full Use → Demonstrate → Apply learning loop for a
  topic. Combines a live demonstration, config walkthrough, and hands-on
  challenge with verification. Usage: /UDA [topic]
allowed-tools: Read, Write, Glob, Grep
user-invocable: true
---

## The UDA Loop

### USE
Use the feature BEFORE explaining it. Let the learner experience it working.

Example for hooks: trigger a hook, let the learner see the PreToolUse
explanation appear, THEN say "Did you notice that? That's a hook."

### DEMONSTRATE
Open the config file. Walk through it. Connect what the learner just saw
to the config that caused it.

### APPLY + CHECK
Set a task. Wait for the learner. Read their file. Give specific pass/fail.
Have them fix issues. Verify. Test live.

Write exercise files to: lessons/$ARGUMENTS/exercises/

## Rules
- USE must happen BEFORE any explanation
- Real files from this repo only
- Follow the APPLY + CHECK pattern (never create files for the learner)
