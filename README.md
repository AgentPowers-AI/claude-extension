<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./assets/logo-darkmode.svg">
    <source media="(prefers-color-scheme: light)" srcset="./assets/logo-lightmode.svg">
    <img alt="AgentPowers" src="./assets/logo-lightmode.svg" width="420">
  </picture>
</p>

<h1 align="center">Claude Desktop Extension</h1>

<p align="center">
  The official AgentPowers marketplace extension for Claude Desktop.<br>
  Search, purchase, and install AI skills directly from your conversations.
</p>

---

## What it does

AgentPowers brings the full marketplace experience into Claude Desktop. You can:

- **Browse** the marketplace by keyword, category, or type (skill/agent)
- **Inspect** skill details, reviews, security scores, and seller profiles
- **Purchase** paid skills via Stripe checkout without leaving Claude
- **Install** skills to any of 12+ supported AI platforms (Claude Code, Cursor, Windsurf, Codex, etc.)
- **Manage** installed skills: check versions, detect edits, find updates, uninstall

## Installation

1. Download `claude-extension.mcpb` from the [latest release](https://github.com/AgentPowers-AI/claude-extension/releases)
2. Drag it into Claude Desktop, or double-click the file
3. Click Install — done!

No terminal, no config files, no Node.js install needed.

### Prerequisites

- **Claude Desktop** with extension support (macOS or Windows)
- **AgentPowers CLI** (`pip install agentpowers`) for install/login operations

## Available Tools

### Discovery

| Tool | Description |
|------|-------------|
| `search_marketplace` | Search skills/agents by keyword, category, or type |
| `search_skills` | Compatibility alias for search_marketplace |
| `get_skill_details` | Get full metadata for a skill by slug |
| `get_categories` | List all marketplace categories with counts |
| `get_seller_profile` | View a seller's profile and published skills |
| `get_skill_reviews` | Read reviews for a specific skill |
| `get_security_results` | View security scan results and trust level |
| `get_platforms` | List all 12+ supported AI platforms |
| `get_marketplace_snapshot` | Quick health check of API, account, and stats |
| `get_openapi_summary` | Summarize the AgentPowers API schema |

### Account

| Tool | Description |
|------|-------------|
| `login_account` | Browser-based login (opens auth page) |
| `logout_account` | Log out and clear credentials |
| `whoami_account` | Show current identity from CLI and API |
| `get_account_profile` | Fetch your full account profile |

### Purchasing

| Tool | Description |
|------|-------------|
| `list_purchases` | List your purchases with license codes |
| `start_checkout` | Create a Stripe checkout session for a paid skill |
| `check_purchase_status` | Poll purchase status; optionally wait and auto-install |
| `confirm_purchase_session` | Confirm purchase by Stripe session ID |
| `download_purchased_skill` | Get download URL for a purchased skill package |

### Installation

| Tool | Description |
|------|-------------|
| `install_skill` | Full automation: detect price, checkout if needed, install |
| `install_purchased_skill` | Install using a previous purchase or license code |
| `check_installed` | List all installed skills with version/edit status |
| `uninstall_skill` | Remove a skill from one or all platforms |
| `check_for_updates` | Compare installed versions against marketplace |

## Example Prompts

**Find a skill for a task:**
> "Search the AgentPowers marketplace for skills that help with code review. Show me the top results with their security scores."

**Install a free skill:**
> "Install the prompt-improver skill from AgentPowers for Claude Code."

**Full purchase workflow:**
> "I want to buy and install the advanced-refactor skill. Log me in if needed, handle the checkout, and install it for Cursor."

## Resources

The extension also exposes MCP resources that Claude can read proactively:

- `agentpowers://marketplace/snapshot` — Live API health, skill count, and account status
- `agentpowers://account/purchases` — Your current purchase list (requires auth)
- `agentpowers://docs/openapi-summary` — Summary of the AgentPowers OpenAPI spec

## Privacy & Security

- **Authentication tokens** are stored locally at `~/.agentpowers/auth.json` and never sent anywhere except the AgentPowers API (`api.agentpowers.ai`).
- **No telemetry** is collected by this extension.
- **Stripe checkout** opens in your default browser; payment details are handled entirely by Stripe and never pass through this extension.
- **Security scans** are performed server-side by AgentPowers on all published skills. Use `get_security_results` to check any skill before installing.

## Configuration

The extension respects these environment variables:

| Variable | Default | Description |
|----------|---------|-------------|
| `AGENTPOWERS_API_BASE` | `https://api.agentpowers.ai/v1` | API base URL |
| `AGENTPOWERS_SITE_ORIGIN` | `https://agentpowers.ai` | Website origin |
| `AGENTPOWERS_API_TOKEN` | — | Override auth token (skips auth.json) |
| `AGENTPOWERS_DEFAULT_TOOL` | `claude-code` | Default install target platform |

## Support

- **Website:** [agentpowers.ai](https://agentpowers.ai/claude-extension)
- **Documentation:** [docs.agentpowers.ai](https://docs.agentpowers.ai)
- **Email:** support@agentpowers.ai
- **GitHub:** [github.com/AgentPowers-AI](https://github.com/AgentPowers-AI)

## License

Copyright 2025-2026 AgentPowers. All rights reserved.
