# claude-skill-dap

Claude Code skills: frontend-design (Anthropic, from anthropics/claude-code), ponytail (DietrichGebert/ponytail, MIT), web-design-guidelines (vercel-labs/agent-skills, MIT), plus MCP servers Context7 (upstash/context7, MIT), Playwright (microsoft/playwright-mcp, Apache-2.0) and GitHub (github/github-mcp-server, MIT).

## Install

In Claude Code:

```
/plugin install ponytail --marketplace Kaleb4B/claude-skill-dap
/plugin install frontend-design --marketplace Kaleb4B/claude-skill-dap
/plugin install web-design-guidelines --marketplace Kaleb4B/claude-skill-dap
/plugin install context7 --marketplace Kaleb4B/claude-skill-dap
/plugin install playwright --marketplace Kaleb4B/claude-skill-dap
/plugin install github --marketplace Kaleb4B/claude-skill-dap
```

On Claude Code older than 2.1.275, add the marketplace first:

```
/plugin marketplace add Kaleb4B/claude-skill-dap
/plugin install ponytail@claude-skill-dap
```

## Context7

The `context7` plugin connects Claude Code to Context7's hosted MCP server (`https://mcp.context7.com/mcp`) for current library documentation. Add `use context7` to a prompt, or put a rule in `CLAUDE.md` such as "Always use Context7 when I need library/API documentation". For higher rate limits, get a free API key at context7.com.

## Playwright

The `playwright` plugin runs `npx @playwright/mcp@latest` locally, so it needs Node.js 18 or newer. Ask Claude to open a page, click through a flow, fill a form or take a screenshot. The browser is installed on first use.

## GitHub

The `github` plugin connects to GitHub's hosted MCP server (`https://api.githubcopilot.com/mcp/`). It reads a personal access token from the `GITHUB_PERSONAL_ACCESS_TOKEN` environment variable, so set it before starting Claude Code:

```bash
export GITHUB_PERSONAL_ACCESS_TOKEN=github_pat_...
```

Create the token at https://github.com/settings/personal-access-tokens/new and grant only the repositories and permissions you need. Never commit it.
