<!--
  SOURCE: https://code.claude.com/docs/en/sub-agents
  FALLBACK: https://code.claude.com/docs/en/agent-teams
  ANTHROPIC TITLE: Subagents + Agent Teams
  LESSON ID: L05
-->

# Lesson 05 — Agents (Subagents)

## What this is
[DESIGN INSTRUCTION: Claude reads both source docs and writes a 2-3 sentence
summary. Must cover: separate Claude instances with own context window,
markdown files in .claude/agents/, tool restrictions, model routing.]

## USE
[NOT sourced from docs — our self-referential moment.]

Claude calls the mentor agent to explain something from a different angle.
The learner sees a different voice respond. "That was the mentor agent. It
has its own context, its own instructions, its own tone. Open the file."

## DEMONSTRATE
[DESIGN INSTRUCTION: Claude opens .claude/agents/mentor.md and teaches
FROM THE DOCS:

Key facts to extract and teach:
- Agent file structure: .claude/agents/<name>.md (from docs)
- All YAML frontmatter fields (from docs):
  - name, description, tools, model, etc.
- How Claude delegates to agents: description matching vs explicit request
  (from docs)
- Fresh context window: agents don't see conversation history (from docs)
- Model routing: different models for different agents (from docs)
- Tool restrictions: agents inherit parent tools if not specified (from docs)
- Agent teams concept: multiple agents coordinating (from agent-teams docs)
- Any built-in agent types or patterns (from docs)

Compare with .claude/agents/reviewer.md in THIS repo:
- Same read-only tools, different personality and purpose
- Reviewer checks work. Mentor asks questions.]

## APPLY + CHECK
Task: Create a custom agent.

Requirements:
- File: .claude/agents/summarizer.md
- name: summarizer
- description: should clearly state when to delegate to it
- tools: Read, Glob only (read-only)
- Instructions: when called, read the specified file and return
  a 3-bullet summary

Check:
- Read .claude/agents/summarizer.md
- Verify it's in .claude/agents/ (not .claude/skills/)
- Verify frontmatter has name, description, tools
- Verify tools are read-only (no Write, no Bash)
- Test: ask Claude to "summarize CLAUDE.md" and see if it delegates
  to the summarizer agent

## Gotchas
[DESIGN INSTRUCTION: Merge docs-sourced gotchas with experience-based ones.

FROM DOCS:
- Extract warnings about context isolation, discovery budget, tool
  inheritance, and cost implications from both docs

FROM EXPERIENCE (validate against docs at build time):
- Each subagent gets a FRESH context window. It doesn't know what you
  just discussed. Everything it needs must be in its prompt or in files.
- Agent descriptions eat into the discovery budget. Keep descriptions precise.
- Agents with no tools restriction inherit all tools. Always specify tools.
- Cost adds up with subagents — use cheaper models for simple tasks.]

## Tips
[DESIGN INSTRUCTION: Merge docs-sourced tips with experience-based ones.

FROM DOCS:
- Extract recommended patterns from both docs

FROM EXPERIENCE:
- Ask Claude to "check with the mentor" — explicit delegation is clearer
  than hoping Claude picks the right agent from the description.
- Agents are great for keeping context clean. Heavy research? Delegate to
  an agent. Only the summary comes back to your main session.]

## Reference
This lesson teaches subagents hands-on. For the complete reference:
→ [Official Claude Code docs: Subagents](https://code.claude.com/docs/en/sub-agents)
→ [Official Claude Code docs: Agent Teams](https://code.claude.com/docs/en/agent-teams)

## What you built
.claude/agents/summarizer.md — a read-only agent that summarizes files.
You now have three agents: mentor (from /setup), reviewer (from /setup),
and summarizer (you built this).

---
*Confused? Type `/explain` to break down what just happened, or `/progress` to see where you are.*
