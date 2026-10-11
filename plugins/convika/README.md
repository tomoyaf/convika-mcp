# Convika for Claude Code

Publish a page Claude wrote, or an HTML file in your repo, to a live URL. Convika hosts the page, stores signups from its form, and counts visits, traffic sources, and button clicks. Claude reads those numbers back to you in the same session.

The plugin connects Claude Code to Convika's hosted MCP server and adds a `publish-page` skill. With the skill, Claude always shows you a private preview first and asks before it publishes.

## Install

In Claude Code:

```
/plugin marketplace add tomoyaf/convika-mcp
/plugin install convika@convika
```

Or from your shell:

```bash
claude plugin marketplace add tomoyaf/convika-mcp
claude plugin install convika@convika
```

Then sign in. Run `/mcp`, select the Convika server, and choose **Authenticate**. A browser window opens where you sign in to Convika or create an account. Sign-in uses OAuth, so there's no API key to copy.

If you added Convika earlier with `claude mcp add`, remove that entry with `claude mcp remove convika` so Claude sees one set of Convika tools.

To remove the plugin, run `claude plugin uninstall convika@convika`.

## Use it

Ask in your own words:

- "Publish landing.html with Convika."
- "Put the page you just wrote online, with a waitlist form."
- "How many people visited the waitlist page this week, and where did they come from?"

Or run the skill with a file: `/convika:publish-page landing.html`

What happens:

1. Claude reads the page and inlines the stylesheets and scripts it loads from your project into one HTML document. Your files stay as they are.
2. Convika saves the document and returns a private preview link that works for 7 days. Claude shows you the link and asks whether to publish, even if you said "publish". Nothing is public yet.
3. Once you've looked at the preview and say "publish it", Convika puts the page on a live URL such as `https://your-page.convika.com`. You can also connect a subdomain of your own, such as `www.example.com`.
4. If the page has a form, Convika stores each submission. Ask Claude for the latest signups, or export them as CSV.

Each save is a new version, so you can roll a live page back in one step.

### What fits on a page

Convika hosts one HTML document per page, so it suits a single static page. A framework build fits only if it's a small static page, about 50 KB of text once inlined.

- Images and videos need `https://` URLs, because Convika doesn't store image or video files.
- Scripts, stylesheets, video, audio, and embeds such as YouTube or Google Maps load from any `https://` URL, and `onclick` handlers run as written.
- On Pro and higher plans, analytics tags from Google Analytics, Google Tag Manager, Microsoft Clarity, Hotjar, Meta Pixel, Plausible, PostHog, Mixpanel, and Cloudflare Web Analytics can send their data. On the Free plan, their data requests are blocked, except image-based ones such as the Meta Pixel's.
- Scripts can't send requests to any other host, and Claude tells you about any request the page makes to one.
- Code that needs `eval`, such as the standard Alpine.js build, doesn't run, so Claude rewrites it in plain JavaScript.
- Forms store text, email, and message fields.

Claude tells you what won't work, and what it changed, before saving.

## Free plan

The Free plan needs no credit card. It includes:

- 10 pages, each with a small "Powered by Convika" badge
- 10,000 page views a month across your pages
- 50 form submissions a month
- 1 custom domain
- The last 10 versions of each page

Paid plans and current limits: https://convika.com/pricing

## What the plugin sends

The plugin contains no code. The skill may ask Claude to run your build, and Claude Code asks you first.

When Claude calls a Convika tool, Claude Code sends that tool's input to `https://mcp.convika.com/mcp`. The input can be the page's HTML and CSS, form fields, conversion goals, or site settings. Convika returns preview and live URLs, visit counts, and form submissions from your Convika account. Claude Code stores your sign-in token on your machine.

The server's tools cover pages, previews, publishing, analytics, forms, and custom domains. Privacy policy: https://convika.com/privacy

## Links

- Docs: https://convika.com/docs
- Support: https://convika.com/support/
- Terms: https://convika.com/terms

## License

MIT
