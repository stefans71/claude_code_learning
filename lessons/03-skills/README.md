<!--
  SOURCE: https://code.claude.com/docs/en/skills
  ANTHROPIC TITLE: Skills
  LESSON ID: L03
-->

# Lesson 03 — Skills

## What this is
[DESIGN INSTRUCTION: Claude reads the source doc and writes a 2-3 sentence
summary of what skills are. Must cover: markdown files in .claude/skills/,
YAML frontmatter + markdown body, create slash commands and specialized behavior.]

## USE
[NOT sourced from docs — our self-referential moment.]

Claude points out: "You typed /lesson. That activated a skill. The file
driving this conversation right now is .claude/skills/lesson/SKILL.md.
Open it."

## DEMONSTRATE
[DESIGN INSTRUCTION: Claude opens .claude/skills/lesson/SKILL.md and teaches
FROM THE DOCS:

Key facts to extract and teach:
- Skill file structure: .claude/skills/<name>/SKILL.md (from docs)
- All YAML frontmatter fields (from docs):
  - name, description, allowed-tools, user-invocable, disable-model-invocation
  - Any other fields documented (context:fork, arguments, etc.)
- How name creates the slash command (from docs)
- How allowed-tools restricts what the skill can do (from docs)
- Skill discovery: descriptions scanned at startup, full content loaded
  on invocation (from docs)
- Description budget and context cost (from docs)
- Backward compatibility: .claude/commands/name.md still works (from docs)
- Supporting files in the skill directory (from docs)

Compare with .claude/skills/setup/SKILL.md in THIS repo:
- Setup has allowed-tools: Read, Write, Glob (needs Write to create files)
- Lesson has Read, Write, Glob, Grep — but Write is only used for
  updating .claude-progress.json when you complete a lesson
- This is "least privilege" — each skill gets the minimum tools it needs]

## APPLY + CHECK
Task: Create a new skill.

Requirements:
- Directory: .claude/skills/hello/SKILL.md
- name: hello
- description: should clearly state when to use it
- allowed-tools: Read only
- Instructions: when invoked, read README.md and give a one-paragraph summary

Check:
- Read .claude/skills/hello/SKILL.md
- Verify it's in the right directory (.claude/skills/hello/, not .claude/commands/)
- Verify frontmatter has name, description, allowed-tools
- Verify allowed-tools is Read only (not Write, not Bash)
- Test: have the learner type /hello and watch it work

## Gotchas
[DESIGN INSTRUCTION: Merge docs-sourced gotchas with experience-based ones.

FROM DOCS:
- Extract warnings about skill/command merging, description budget,
  lazy loading, and any other caveats

FROM EXPERIENCE (validate against docs at build time):
- Skill descriptions have a context budget (~1% of context window). Too many
  skills = truncated descriptions = Claude can't match them.
- The description field is how Claude decides when to auto-invoke. Write it
  like you'd describe the task to a coworker.]

## Tips
[DESIGN INSTRUCTION: Merge docs-sourced tips with experience-based ones.

FROM DOCS:
- Extract any recommended practices from the skills docs

FROM EXPERIENCE:
- Test your description: ask Claude to do the task WITHOUT typing the slash
  command. If Claude doesn't find the skill, your description needs work.
- Keep SKILL.md under 500 lines. Add reference files in the skill directory
  if you need more.
- Use disable-model-invocation: true for skills that should ONLY run when
  you type the command (not auto-detected).]

## Reference
This lesson teaches skills hands-on. For the complete reference:
→ [Official Claude Code docs: Skills](https://code.claude.com/docs/en/skills)

## What you built
.claude/skills/hello/SKILL.md — a working slash command you created from scratch.

---
*Confused? Type `/explain` to break down what just happened, or `/progress` to see where you are.*
