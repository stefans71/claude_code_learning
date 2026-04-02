<!--
  SOURCE: https://code.claude.com/docs/en/mcp
  ANTHROPIC TITLE: Connect Claude Code to tools via MCP
  LESSON ID: L06
-->

# Lesson 06 — MCP (Model Context Protocol)

## What this is
[DESIGN INSTRUCTION: Claude reads the source doc and writes a 2-3 sentence
summary. Must cover: MCP servers extend Claude's capabilities, configured in
.mcp.json, connect to external tools and services.]

## USE
[Claude simulates what an MCP interaction looks like. No server is configured
yet — this is intentional. Claude explains: "I'm about to show you what it
looks like when Claude has MCP tools. Right now I don't have any connected.
Watch what happens when I try to fetch a URL..."

Claude attempts a fetch, shows the lack of MCP tools, then runs /context
to show the baseline token usage with zero MCP servers.]

"First, let me show you where we are on context usage — zero MCP servers."
[runs /context, shows token breakdown with no MCP overhead]

## DEMONSTRATE
[DESIGN INSTRUCTION: Claude teaches MCP configuration FROM THE DOCS:

Key facts to extract and teach:
- .mcp.json file structure: mcpServers object (from docs)
- Server config fields: type, command, args, env (from docs)
- Project vs user scope for MCP config (from docs)
- How to add/remove servers: `claude mcp add`, `claude mcp remove` (from docs)
- Tool Search / deferred tool loading (from docs)
- /mcp command to manage servers mid-session (from docs)
- /context command to see MCP token cost (from docs)
- Any security considerations from docs

Connect to THIS repo's context: no MCP servers configured yet.
This is the first time in the tutorial that we introduce a file that makes
network calls. Everything before this was local-only. .mcp.json tells Claude
to run external commands (like npx) that download and execute third-party code.
This is an opt-in decision.]

## APPLY + CHECK
Task: Create a .mcp.json file with a fetch MCP server configuration.

**This is opt-in.** Tell the learner:
"This exercise creates a file that will make network calls. The fetch server
uses npx to download and run @anthropic-ai/mcp-server-fetch. If you'd rather
not do that, you can create the config file for practice without testing it
live — the structure is the lesson."

Requirements:
- File: .mcp.json at project root (NOT in .claude/)
- Must contain the fetch server configuration:
  ```json
  {
    "mcpServers": {
      "fetch": {
        "type": "stdio",
        "command": "npx",
        "args": ["-y", "@anthropic-ai/mcp-server-fetch"]
      }
    }
  }
  ```
- Must be valid JSON

Check:
- Read .mcp.json
- Verify it's at project root
- Verify valid JSON (no trailing commas)
- Verify fetch server config structure is correct
- If the learner wants to test live: they need to restart the session
  for MCP to load, then ask Claude to fetch a URL
- Run /context after restart to show the MCP token cost delta

## Gotchas
[DESIGN INSTRUCTION: Merge docs-sourced gotchas with experience-based ones.

FROM DOCS:
- Extract warnings about token cost, server management, scoping, and
  any other caveats from the MCP docs

FROM EXPERIENCE (validate against docs at build time):
- MCP servers eat tokens EVEN WHEN YOU DON'T USE THEM. Tool definitions load
  on every message. A 5-server setup can burn 50,000+ tokens before you type.
- /mcp lets you disable servers mid-session, BUT disabled servers may
  auto-reconnect on next session. To truly remove: `claude mcp remove [name]`.
- .mcp.json at project root loads for EVERYONE who clones the repo. If you
  commit servers that need auth tokens, collaborators get connection errors.
- The "good default is zero MCP servers connected." Add when needed, remove
  when done. Think of MCP like browser tabs — each one has overhead.]

## Tips
[DESIGN INSTRUCTION: Merge docs-sourced tips with experience-based ones.

FROM DOCS:
- Extract recommended practices from the MCP docs

FROM EXPERIENCE:
- Before adding an MCP server, ask: "Can I do this with a bash command?"
  gh CLI instead of GitHub MCP, curl instead of fetch MCP.
- Run /context before and after adding a server. See the delta.
- Limit to 3-5 essential servers. Be ruthless.
- For one-off needs, add the server, do the task, remove it.]

## Reference
This lesson teaches MCP hands-on. For the complete reference:
→ [Official Claude Code docs: MCP](https://code.claude.com/docs/en/mcp)

## What you built
.mcp.json — an MCP configuration file. Even if you can't test it live,
you understand the format, the gotchas, and the token cost tradeoff.

---
*Confused? Type `/explain` to break down what just happened, or `/progress` to see where you are.*
