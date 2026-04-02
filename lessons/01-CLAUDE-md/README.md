<!--
  SOURCE: https://code.claude.com/docs/en/memory
  ANTHROPIC TITLE: How Claude remembers your project
  LESSON ID: L01
-->

# Lesson 01 — CLAUDE.md

## What this is
[DESIGN INSTRUCTION: Claude reads the source doc and writes a 2-3 sentence
plain English summary of what CLAUDE.md is. Must cover: it's a markdown file,
Claude reads it every session, it sets persistent context. Use the doc's own
framing: "context, not enforced configuration."]

## USE
[NOT sourced from docs — this is our self-referential teaching moment.]

"You've been inside this feature since you typed /setup. The CLAUDE.md at the
root of this repo? Claude read it before you said a word. That's why I've been
explaining my actions — the CLAUDE.md told me to."

Claude points out that the learner has been inside a CLAUDE.md since they
opened the project. This repo's CLAUDE.md has been active since /setup.

## DEMONSTRATE
[DESIGN INSTRUCTION: Claude opens ./CLAUDE.md in the editor and walks through
each section. Then teaches the following FROM THE DOCS:

Key facts to extract and teach:
- CLAUDE.md is delivered as a user message after the system prompt, not part
  of the system prompt (docs: "no guarantee of strict compliance")
- File locations and scope hierarchy (from the docs table):
  - Managed policy (org-wide, IT-deployed)
  - Project: ./CLAUDE.md or ./.claude/CLAUDE.md
  - User: ~/.claude/CLAUDE.md
  - All stack — they don't replace each other
- 200-line target per file (from docs)
- @path import syntax with 5-hop recursion limit (from docs)
- .claude/rules/ for path-specific rules with YAML frontmatter (from docs)
- Auto memory: Claude writes its own notes, stored in
  ~/.claude/projects/<project>/memory/ (from docs)
- HTML comments are stripped from CLAUDE.md before injection (from docs)
- /memory command to browse loaded files (from docs)

Connect each fact to something the learner can observe in THIS repo.]

## APPLY + CHECK
Task: Create a CLAUDE.local.md file in the project root.

Requirements:
- Must be a personal note file (gitignored — check .gitignore to verify)
- Should contain at least 3 personal instructions for Claude
  (e.g., "I prefer short answers", "I'm learning Python", "explain acronyms")
- Must NOT duplicate what's already in CLAUDE.md
- Instructions must be specific enough to verify (per the docs:
  "Use 2-space indentation" not "format code properly")

Check:
- Read CLAUDE.local.md
- Verify it exists at project root (not in .claude/)
- Verify it has at least 3 distinct instructions
- Verify .gitignore includes CLAUDE.local.md
- Verify instructions don't duplicate the main CLAUDE.md
- Verify instructions are specific (not vague)

Then test: ask Claude something and see if the personal instructions
affect the response style.

## Gotchas
[DESIGN INSTRUCTION: Merge docs-sourced gotchas with experience-based ones.

FROM DOCS:
- CLAUDE.md is context, not enforcement. Claude reads it and tries to follow
  it, but there's no guarantee of strict compliance, especially for vague or
  conflicting instructions.
- Files over 200 lines consume more context and may reduce adherence.
- If two rules contradict, Claude may pick one arbitrarily.
- Subdirectory CLAUDE.md files only load when Claude reads files in that
  directory, not at launch.
- Instructions seem lost after /compact? CLAUDE.md fully survives compaction.
  If an instruction disappeared, it was given only in conversation, not written
  to CLAUDE.md.
- Auto memory MEMORY.md: first 200 lines or 25KB loaded. Beyond that, not
  loaded at session start.

FROM EXPERIENCE (validate against docs at build time):
- Stale instructions from old projects cause confusing behavior. Review your
  CLAUDE.md when things feel off.
- CLAUDE.md is read-only context. Claude can't update it during a session
  unless you explicitly ask it to edit the file.
- There's a hierarchy: ~/.claude/CLAUDE.md (global) → project CLAUDE.md →
  CLAUDE.local.md. They STACK — all three are read.]

## Tips
[DESIGN INSTRUCTION: Merge docs-sourced tips with experience-based ones.

FROM DOCS:
- Run /memory to see all loaded CLAUDE.md files and auto memory.
- Use @path imports to keep CLAUDE.md under 200 lines.
- Use .claude/rules/ for path-specific instructions.
- Run /init to auto-generate a starting CLAUDE.md.
- Use InstructionsLoaded hook to debug which files load and when.
- HTML comments (<!-- -->) are stripped — use them for maintainer notes.

FROM EXPERIENCE:
- Front-load the most important instructions. Claude weighs early content
  more heavily in long context.
- Use CLAUDE.local.md for personal preferences you don't want to inflict
  on collaborators.
- Before running /compact, tell Claude to summarize the session state,
  then use that summary as the /compact note.]

## Reference
This lesson teaches CLAUDE.md hands-on. For the complete reference:
→ [Official Claude Code docs: How Claude remembers your project](https://code.claude.com/docs/en/memory)

## What you built
CLAUDE.local.md — your personal instructions file. It persists across sessions
and is gitignored so it doesn't affect anyone else.

---
*Confused? Type `/explain` to break down what just happened, or `/progress` to see where you are.*
