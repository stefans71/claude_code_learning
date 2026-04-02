<!--
  SOURCE: https://code.claude.com/docs/en/settings
  ANTHROPIC TITLE: Settings
  LESSON ID: L02
-->

# Lesson 02 — settings.json

## What this is
[DESIGN INSTRUCTION: Claude reads the source doc and writes a 2-3 sentence
summary of what settings.json is. Must cover: project-scoped configuration,
lives in .claude/, controls hooks and permissions, can be shared or local.]

## USE
[NOT sourced from docs — our self-referential moment.]

Claude runs /context to show the learner what's loaded. Points out the hooks
that have been annotating actions since /setup. "Those explanations before
every action? They come from a 15-line JSON file."

## DEMONSTRATE
[DESIGN INSTRUCTION: Claude opens .claude/settings.json and teaches FROM DOCS:

Key facts to extract and teach:
- Settings file locations and priority hierarchy (from docs):
  1. .claude/settings.local.json (personal project — gitignored)
  2. .claude/settings.json (shared project)
  3. ~/.claude/settings.local.json (personal global)
  4. ~/.claude/settings.json (global)
- All available settings keys (from docs — permissions, hooks, env vars, etc.)
- Hook types: "prompt" vs "command" (from docs)
- Hook events: PreToolUse, PostToolUse, SessionStart, Stop, etc. (from docs)
- Matcher syntax for hooks (from docs)
- How settings.local.json overrides settings.json (from docs — shallow merge)
- Permissions section: allowedTools, blockedTools (from docs)

Connect to THIS repo: the hooks the learner has been seeing since /setup
are configured in this exact file.]

## APPLY + CHECK
Task: Add a new hook to .claude/settings.json.

Requirements:
- Add a SessionStart hook
- type: "prompt"
- The prompt should tell Claude to greet the learner by checking
  .claude-progress.json and mentioning their current lesson

Check:
- Read .claude/settings.json
- Verify SessionStart hook exists
- Verify type is "prompt" (not "command")
- Verify the prompt references .claude-progress.json
- Test: tell the learner to start a new session (/clear then resume)
  and see if the greeting appears

## Gotchas
[DESIGN INSTRUCTION: Merge docs-sourced gotchas with experience-based ones.

FROM DOCS:
- Extract any warnings, caveats, or edge cases from the settings docs

FROM EXPERIENCE (validate against docs at build time):
- Project vs user scope: editing ~/.claude/settings.json changes EVERY project.
  The file in .claude/ is project-scoped. Know which one you're editing.
- settings.local.json overrides settings.json on the keys it sets. No deep
  merge — it's a shallow key replacement.
- Hooks in settings.json fire on every matching action. That's context cost.
  A verbose PreToolUse prompt on every Write|Edit|Bash adds up in long sessions.]

## Tips
[DESIGN INSTRUCTION: Merge docs-sourced tips with experience-based ones.

FROM DOCS:
- Extract any recommended practices from the settings docs
- /hooks command to inspect registered hooks

FROM EXPERIENCE:
- Use /context regularly to see what's eating your token budget.
- Before running /compact, tell Claude to summarize, then use that as
  the /compact note.
- Use /hooks inside Claude Code to see all configured hooks at a glance.]

## Reference
This lesson teaches settings.json hands-on. For the complete reference:
→ [Official Claude Code docs: Settings](https://code.claude.com/docs/en/settings)

## What you built
A SessionStart hook that personalizes your greeting. Your settings.json now
has three hooks — two from /setup, one you wrote yourself.

---
*Confused? Type `/explain` to break down what just happened, or `/progress` to see where you are.*
