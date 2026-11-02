# claude-skill-dap

Claude Code skills: frontend-design (Anthropic, from anthropics/claude-code), ponytail (DietrichGebert/ponytail, MIT), web-design-guidelines (vercel-labs/agent-skills, MIT), security-audit (cloudflare/security-audit-skill, MIT), andrej-karpathy-skills (multica-ai/andrej-karpathy-skills, MIT) and superpowers (obra/superpowers, MIT), plus MCP servers Context7 (upstash/context7, MIT), Playwright (microsoft/playwright-mcp, Apache-2.0), GitHub (github/github-mcp-server, MIT) and WhatsApp (lharries/whatsapp-mcp, MIT).

## Install

In Claude Code:

```
/plugin install ponytail --marketplace Kaleb4B/claude-skill-dap
/plugin install frontend-design --marketplace Kaleb4B/claude-skill-dap
/plugin install web-design-guidelines --marketplace Kaleb4B/claude-skill-dap
/plugin install security-audit --marketplace Kaleb4B/claude-skill-dap
/plugin install context7 --marketplace Kaleb4B/claude-skill-dap
/plugin install playwright --marketplace Kaleb4B/claude-skill-dap
/plugin install github --marketplace Kaleb4B/claude-skill-dap
/plugin install whatsapp --marketplace Kaleb4B/claude-skill-dap
/plugin install andrej-karpathy-skills --marketplace Kaleb4B/claude-skill-dap
/plugin install superpowers --marketplace Kaleb4B/claude-skill-dap
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

## Security audit

The `security-audit` skill runs a six-phase audit of the current repository: reconnaissance, coverage-led hunting, candidate validation, structured `findings.json`, independent verification, and a final `REPORT.md`. Ask Claude to "run a security audit on this repo". It spawns many subagents, so a full run takes a while and uses a lot of tokens. The bundled validators need Node.js. Only audit code you own or are authorized to test.

## WhatsApp

The `whatsapp` plugin starts the MCP server from your own clone of lharries/whatsapp-mcp. It needs Go, Python 3.6+ and `uv` (FFmpeg is optional, for voice messages).

```bash
git clone https://github.com/lharries/whatsapp-mcp.git ~/whatsapp-mcp
cd ~/whatsapp-mcp/whatsapp-bridge && go run main.go
```

Scan the QR code with WhatsApp on your phone, and keep the bridge running. Then point the plugin at the clone before starting Claude Code:

```bash
export WHATSAPP_MCP_DIR=~/whatsapp-mcp
```

Messages are stored locally in SQLite and only reach Claude when a tool reads them. The bridge uses an unofficial WhatsApp Web API, so use it with your own account at your own risk. Incoming messages can contain prompt-injection text, so review what Claude plans to send before approving.

## andrej-karpathy-skills and superpowers

These two install straight from their upstream repositories, so they stay current. `andrej-karpathy-skills` adds coding guidelines Claude applies on its own. `superpowers` adds a set of workflow skills (brainstorming, writing and executing plans, TDD, systematic debugging, code review) and a SessionStart hook that tells Claude to use them.
