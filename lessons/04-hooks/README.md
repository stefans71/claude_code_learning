<!--
  SOURCE: https://code.claude.com/docs/en/hooks
  FALLBACK: https://code.claude.com/docs/en/hooks-guide
  ANTHROPIC TITLE: Hooks (reference + guide)
  LESSON ID: L04
-->

# Lesson 04 — Hooks

## What this is
[DESIGN INSTRUCTION: Claude reads both source docs and writes a 2-3 sentence
summary. Must cover: automated actions at lifecycle points, configured in
settings.json, deterministic (unlike CLAUDE.md which is a request).]

## USE
[NOT sourced from docs — our self-referential moment.]

Claude points at the PreToolUse annotations that have been appearing since
session start. "Those explanations before my actions? That's a hook. It's
been running since /setup. Here's the 15-line config that makes it happen."

Show the difference: CLAUDE.md says "explain your actions" (a request).
The PreToolUse hook MAKES Claude explain (deterministic).

## DEMONSTRATE
[DESIGN INSTRUCTION: Claude opens .claude/settings.json and teaches FROM DOCS:

Key facts to extract and teach:
- All hook event types (from docs): PreToolUse, PostToolUse, SessionStart,
  Stop, SubagentStop, etc.
- Hook type options: "prompt", "command", "agent" (from docs)
- Matcher syntax: tool name matching, pipe-separated (from docs)
- Hook configuration structure in settings.json (from docs)
- Exit code behavior for command hooks: 0=allow, 2=block (from docs)
- The "if" field for conditional hooks (from docs — if it exists)
- How prompt hooks inject instructions into Claude's context (from docs)
- How command hooks execute shell scripts (from docs — explain security
  implications, note that THIS project only uses "prompt" type)

Connect to THIS repo: walk through the PreToolUse and PostToolUse hooks
that /setup created. Show matcher, type, prompt text.]

## APPLY + CHECK
Task: Create a custom PostToolUse hook.

Requirements:
- Add to .claude/settings.json (don't break existing hooks)
- Matcher: "Bash" only
- type: "prompt"
- The prompt should make Claude note the exit code and whether the
  command succeeded or failed after every Bash execution

Check:
- Read .claude/settings.json
- Verify valid JSON (common mistake: trailing commas)
- Verify new hook is under PostToolUse, not PreToolUse
- Verify matcher is "Bash" (not "bash" — case sensitive!)
- Verify type is "prompt" (not "command")
- Test: ask Claude to run a simple bash command and watch the
  new annotation appear afterward

## Gotchas
[DESIGN INSTRUCTION: Merge docs-sourced gotchas with experience-based ones.

FROM DOCS:
- Extract all warnings, edge cases, and caveats from both hooks docs
- Especially: matcher case sensitivity, exit codes, event firing frequency

FROM EXPERIENCE (validate against docs at build time):
- type: "command" hooks run shell scripts. type: "prompt" hooks send
  instructions to Claude. For security, we only use "prompt" in this project.
- Stop hooks fire whenever Claude finishes responding — not just at "task
  completion." If Claude responds three times, Stop fires three times.
- Prompt hooks add context cost on every matching action. Keep prompts short.]

## Tips
[DESIGN INSTRUCTION: Merge docs-sourced tips with experience-based ones.

FROM DOCS:
- /hooks command to inspect registered hooks
- Any recommended patterns from the hooks guide

FROM EXPERIENCE:
- Use /hooks to see all registered hooks grouped by event.
- "agent" type hooks delegate to a subagent for evaluation — advanced pattern.]

## Reference
This lesson teaches hooks hands-on. For the complete reference:
→ [Official Claude Code docs: Hooks](https://code.claude.com/docs/en/hooks)
→ [Official Claude Code docs: Hooks Guide](https://code.claude.com/docs/en/hooks-guide)

## What you built
A PostToolUse Bash hook that reports command success/failure. Your
settings.json now has hooks you wrote alongside hooks /setup created.

---
*Confused? Type `/explain` to break down what just happened, or `/progress` to see where you are.*
