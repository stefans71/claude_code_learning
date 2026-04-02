<!--
  SOURCE: https://code.claude.com/docs/en/common-workflows
  FALLBACK: https://code.claude.com/docs/en/best-practices
  ANTHROPIC TITLE: Common Workflows + Best Practices
  LESSON ID: L07
-->

# Lesson 07 — Putting It Together

## What this is
[DESIGN INSTRUCTION: Claude reads both source docs and writes a 2-3 sentence
summary. Frame as: every feature works as a system. This lesson shows the
whole picture and teaches real-world workflow patterns.]

## USE
[NOT sourced from docs — our self-referential moment.]

Claude runs /context and narrates every section: system prompt, system tools,
MCP tools, custom agents, memory files, messages, free space. Maps each one
to a lesson the learner completed.

## DEMONSTRATE
[DESIGN INSTRUCTION: Two parts.

PART 1 — Self-referential walkthrough (our design):
Open every config file the learner has created or modified:
- CLAUDE.md → lesson 01 (the briefing)
- CLAUDE.local.md → lesson 01 (personal notes)
- .claude/settings.json → lesson 02 + 04 (settings + hooks)
- .claude/skills/hello/SKILL.md → lesson 03 (their first skill)
- .claude/agents/summarizer.md → lesson 05 (their first agent)
- .mcp.json → lesson 06 (if it exists)

Walk through how they interact:
"When you start a session, Claude reads CLAUDE.md. Then settings.json
loads hooks. Then skills are discovered from their descriptions. Then
MCP servers connect. Then agents are registered. By the time you type
your first message, all of this is already active."

PART 2 — Workflow patterns FROM DOCS:
Key facts to extract and teach from common-workflows:
- Common workflow patterns (from docs)
- Context management strategies (from docs)
- /compact usage and strategies (from docs)
- Session management: /clear, /resume, /rename (from docs)

Key facts from best-practices:
- Recommended project setup patterns (from docs)
- Performance and context budget tips (from docs)
- Team collaboration patterns (from docs)]

## APPLY + CHECK
Task: Create a complete mini-project configuration from scratch.

Requirements:
- Create a new directory: practice-project/ (inside this repo, gitignored)
- In it, create:
  - CLAUDE.md with project context (at least 5 instructions)
  - .claude/skills/review/SKILL.md (a code review skill)
  - .claude/settings.json with at least one hook
- All files must be valid and follow the conventions learned

Check:
- Read all three files
- Verify CLAUDE.md is at the project root of practice-project/
- Verify the skill is in the right directory with valid frontmatter
- Verify settings.json has valid JSON with at least one hook
- Verify the skill has appropriate tool restrictions

Then verify from THIS session (the tutorial can read inside practice-project/):
- Read all three files and check requirements above
- Once all pass, tell the learner to test it live:
  "Open a new terminal, cd into practice-project/, and run `claude`.
  Type `/review` to test your skill, and try any action to see your
  hook fire. When you're done, come back here."
- The practice project is gitignored so it won't pollute the tutorial repo

## Gotchas
[DESIGN INSTRUCTION: Merge docs-sourced gotchas with experience-based ones.

FROM DOCS:
- Extract warnings and caveats from both common-workflows and best-practices

FROM EXPERIENCE (validate against docs at build time):
- /compact preserves context but loses detail. Summarize first, then compact.
- /clear is nuclear. Use /rename first to save the session.
- Long sessions degrade. If Claude forgets things from 30 minutes ago,
  that's context pressure. Compact or start fresh.
- Everything costs context: CLAUDE.md, hooks, agent descriptions, MCP tools,
  conversation history. /context shows where your budget is going.]

## Tips
[DESIGN INSTRUCTION: Merge docs-sourced tips with experience-based ones.

FROM DOCS:
- Extract recommended practices from both docs

FROM EXPERIENCE:
- The strongest setups are minimal. Clean CLAUDE.md under 200 lines,
  3-5 focused skills, 1-2 agents, hooks only where you need enforcement.
- Version control your .claude/ config (except secrets and local overrides).
- When starting a new project, run /context immediately. See what's loaded.
- Use subagents for heavy exploration — the summary comes back without
  the intermediate noise eating your context.]

## Reference
This lesson ties everything together. For workflow patterns and best practices:
→ [Official Claude Code docs: Common Workflows](https://code.claude.com/docs/en/common-workflows)
→ [Official Claude Code docs: Best Practices](https://code.claude.com/docs/en/best-practices)

## What you built
A complete mini-project configuration: CLAUDE.md, skill, and settings.json
working together. You understand every file in a Claude Code project because
you've built each one yourself.

---
*Confused? Type `/explain` to break down what just happened, or `/progress` to see where you are.*
