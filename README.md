# Convika MCP Server

> Publish AI-made landing pages on your own domain, with a signup form and visitor stats.

mcp-name: com.convika/convika

[Convika](https://convika.com) hosts landing pages made with AI. You can upload the HTML file ChatGPT, Claude, or Gemini wrote, generate a page in the dashboard, or connect your AI client here and let it save and publish the page for you. A page can carry a form that keeps every entry, and every page gets visitor stats: visits, traffic sources, UTM campaigns, button clicks, and signups.

This repository holds the public documentation and the server manifest for the **hosted** Convika MCP server. The service itself is closed source.

- **MCP endpoint**: `https://mcp.convika.com/mcp` (Streamable HTTP, OAuth 2.1)
- **Official MCP Registry**: [`com.convika/convika`](https://registry.modelcontextprotocol.io/v0.1/servers?search=com.convika/convika)
- **Docs**: https://convika.com/docs/
- **Sign up (free, no card)**: https://app.convika.com/signup

## Quick start

### Claude (web and desktop)

1. Settings → **Connectors** → **Add custom connector**
2. Enter `https://mcp.convika.com`
3. Sign in to your Convika account, or create one for free

### Claude Code

```bash
claude mcp add --transport http convika https://mcp.convika.com
```

### Codex, Cursor, and other MCP clients

```json
{
  "mcpServers": {
    "convika": {
      "url": "https://mcp.convika.com/mcp"
    }
  }
}
```

ChatGPT can connect in developer mode with the same URL.

Sign-in uses OAuth 2.1 with dynamic client registration and PKCE. Your client opens a browser window to sign in, so there are no API keys to manage.

## What your AI can do

| Area | Tools |
|---|---|
| Create and edit pages | `create_landing_page_preview`, `create_landing_page`, `create_site`, `list_sites`, `get_site`, `update_site`, `save_page_content`, `get_page_structure` |
| Preview and publish | `create_preview`, `publish_site`, `rollback_site`, `unpublish_site`, `create_claim_code` |
| Forms and goals | `create_form`, `get_form_submissions`, `export_form_submissions`, `set_goals`, `list_goals` |
| Visitor stats | `get_analytics_summary`, `get_analytics_detail`, `get_portfolio_analytics`, `analyze_site_performance`, `analyze_source_quality`, `query_timeseries`, `query_segments`, `query_cta_performance`, `detect_trend` |
| Domains and URLs | `set_site_url`, `setup_custom_domain`, `get_domain_status`, `list_domain_routes`, `disable_domain_route`, `start_domain_control_verification`, `check_domain_control_verification`, `activate_domain_handover` |
| Other | `ping`, `get_referral_link` |

The usual flow: your AI writes the page and calls `create_landing_page_preview`, which returns a private preview link. Nothing goes live until you ask it to publish. Each save is a new version, so a rollback is one call. Published pages keep serving even if the dashboard is down.

## Example prompts

> "Make a landing page for my coffee shop's opening with a signup form, and show me the preview."

> "Publish it."

> "How did the page do this week? Which source brought the most signups?"

> "Put this page on www.mycoffeeshop.com."

## Plans

- **Free**: $0, no credit card. 10 pages, 10,000 pageviews a month, 50 form entries a month, 1 custom domain (a subdomain such as `www`), 90 days of visitor stats, and a small "Powered by Convika" badge.
- **Pro**: $12 a month, or $108 a year. 50 pages, unlimited form entries and custom domains, no badge, and a 14-day free trial.

Details: https://convika.com/pricing/

## Support

- Problems with the MCP server or these docs: open an issue in this repository.
- Product support: https://convika.com/support/
