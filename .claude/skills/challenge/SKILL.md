---
name: challenge
description: Get a hands-on task harder than the lesson exercise.
  Generates a challenge based on the most recently completed lesson
  or a specific topic if provided. Usage: /challenge [optional topic]
allowed-tools: Read, Glob, Grep
user-invocable: true
---

## What you do

1. Read .claude-progress.json to find the most recent completed lesson
   (or use $ARGUMENTS if provided)
2. Generate a challenge that's harder than the lesson's APPLY exercise
3. The challenge must require creating or modifying a REAL file
4. State clear requirements the learner must meet
5. When they say they're done, read their work and check it
6. Follow the same pass/fail pattern as lessons

## Challenge design rules
- Must be testable — the learner can see it work (or not)
- Must use the feature from the lesson, not just describe it
- Should combine with something from a previous lesson when possible
- Give constraints: "under 20 lines", "read-only tools only", etc.

## Rules
- Do NOT create files for the learner
- Do NOT give the solution, only hints when stuck
- Challenges should take 5-15 minutes
