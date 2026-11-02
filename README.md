# claude-skill-dap

Claude Code skills: frontend-design (Anthropic, from anthropics/claude-code), ponytail (DietrichGebert/ponytail, MIT), web-design-guidelines (vercel-labs/agent-skills, MIT) and the Context7 MCP server (upstash/context7, MIT).

## Install

In Claude Code:

```
/plugin install ponytail --marketplace Kaleb4B/claude-skill-dap
/plugin install frontend-design --marketplace Kaleb4B/claude-skill-dap
/plugin install web-design-guidelines --marketplace Kaleb4B/claude-skill-dap
/plugin install context7 --marketplace Kaleb4B/claude-skill-dap
```

On Claude Code older than 2.1.275, add the marketplace first:

```
/plugin marketplace add Kaleb4B/claude-skill-dap
/plugin install ponytail@claude-skill-dap
```

## Context7

The `context7` plugin connects Claude Code to Context7's hosted MCP server (`https://mcp.context7.com/mcp`) for current library documentation. Add `use context7` to a prompt, or put a rule in `CLAUDE.md` such as "Always use Context7 when I need library/API documentation". For higher rate limits, get a free API key at context7.com.
