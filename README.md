# Convika MCP Server

> Your AI can ship landing pages now.

mcp-name: com.convika/convika

[Convika](https://convika.com) is a landing page platform built for MCP clients. Connect from Claude, Codex, or any MCP-compatible AI client and your AI handles the full landing page lifecycle: create, preview, publish, measure, and iterate — by just describing what you want.

This repository hosts the public documentation and server manifest for the **hosted** Convika MCP server. The service itself is closed-source.

- **MCP endpoint**: `https://mcp.convika.com/mcp` (Streamable HTTP, OAuth 2.1)
- **Official MCP Registry**: [`com.convika/convika`](https://registry.modelcontextprotocol.io/v0.1/servers?search=com.convika/convika)
- **Website / docs**: https://convika.com/docs
- **Sign up (free)**: https://app.convika.com/signup

## Quick start

### Claude Desktop

1. Settings → **Connectors** → **Add custom connector**
2. Enter `https://mcp.convika.com`
3. Authenticate with your Convika account (free to create)

### Claude Code

```bash
claude mcp add --transport http convika https://mcp.convika.com
```

### Generic MCP client config

```json
{
  "mcpServers": {
    "convika": {
      "url": "https://mcp.convika.com/mcp"
    }
  }
}
```

Authentication is OAuth 2.1 with dynamic client registration — your client will open a browser window to sign in. No API keys to manage.

## What your AI can do

| Area | Tools |
|---|---|
| Pages | `create_landing_page`, `create_site`, `list_sites`, `get_site`, `update_site`, `save_page_content` |
| Publishing | `create_preview`, `publish_site`, `rollback_site`, `unpublish_site` |
| Analytics | `get_analytics_summary`, `get_analytics_detail`, `get_portfolio_analytics`, `analyze_site_performance`, `analyze_source_quality` |
| Forms & goals | `create_form`, `get_form_submissions`, `export_form_submissions`, `set_goals`, `list_goals` |
| Domains | `setup_custom_domain`, `get_domain_status` |
| Misc | `ping`, `get_referral_link` |

Published pages are served from a global edge network and keep serving even if the dashboard is down. Every save creates a new version; rollback is one step.

## Example prompts

> "Create a landing page for my coffee shop with a hero, three feature cards, and a contact form. Show me the preview."

> "Publish it to production."

> "How is my page performing this week? Which traffic source converts best?"

> "Connect www.example.com to this page."

## Plans

Free plan available; paid plans add traffic, sites, form submissions, custom domains, and team members. See https://convika.com/pricing.

## Support

- Issues with the MCP server or docs: open an issue in this repository
- Product support: https://convika.com
