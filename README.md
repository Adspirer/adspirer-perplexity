# Adspirer for Perplexity

AI advertising agent for growing your business. Create, analyze, and optimize ad campaigns across Google, Meta, TikTok, LinkedIn, Amazon, and ChatGPT Ads—with your approval.

This package connects Perplexity to the hosted Adspirer MCP server and gives its agent the
skills to use it well. It covers Google, Meta, TikTok, LinkedIn, Amazon and ChatGPT Ads. It can change ad accounts, and only with your approval: campaigns are built paused, every change is shown first and read back afterwards.

## What's included

| File | Purpose |
| --- | --- |
| [connector.json](connector.json) | Connector details: name, URL, sign-in, logo, links |
| [LISTING.md](LISTING.md) | Paste-ready name, descriptions and submission notes |
| [AGENT.md](AGENT.md) | Agent instructions to paste into Perplexity |
| `skills/` | 14 Agent Skills (`SKILL.md` folders) |
| `dist/skills/` | The same skills as one zip each, for upload |
| `examples/` | Agent API request examples |

## Connect in Perplexity

1. Open **Settings → Connectors** and choose **Custom connector → Remote**.
2. Name it `Adspirer` and enter the URL `https://mcp.adspirer.com/mcp`.
3. Sign in with your Adspirer account in the browser window.
4. Connect your ad accounts at https://adspirer.ai/connections.

Custom connectors are reported to need a paid Perplexity plan, and admin permission in
organizations. Menu labels change; check Perplexity's help center if yours differ.

## Use with the Perplexity Agent API

A Project administrator adds the server once on the Project connectors page in the API Console
(server name, MCP URL, authentication, transport **Streamable HTTP**), then copies the connector
ID. Requests reference it by ID; see [examples/agent_api.py](examples/agent_api.py) and
[examples/agent_api.sh](examples/agent_api.sh).

Open question: Perplexity's documentation lists **API Key or None** as the authentication choices
for custom connectors in the API Console, and Adspirer signs in with browser OAuth. This has not
been tested. If OAuth is not offered there, ask Perplexity (api@perplexity.ai) before relying on
the Agent API route; the app route above is the supported one.

Agent API connector calls run **without approval by default**. This connector can change ad accounts, so the examples set an approval policy and you should keep one on every request.

## Add the skills

Perplexity Computer is reported to import Agent Skills (`SKILL.md` folders); this has not been
tested with these skills. Each skill is in `skills/` and zipped in `dist/skills/`. Where skills
are not available, paste [AGENT.md](AGENT.md) into the Space or Computer instructions instead.

| Skill | Use it for |
| --- | --- |
| `adspirer-agent` | Paid-media advertising agent behavior for Adspirer — create, analyze, and optimize ad campaigns across Google Ads, Meta, TikTok, LinkedIn, Amazon, and ChatGPT Ads. Use for any request about ads, campaigns, budgets, keywords, creative, spend, ROAS, CPA, or ad performance. Sets the safety rules (campaigns are created paused, confirm before spending) and routes to the right Adspirer skill. |
| `adspirer-amazon-ads` | Create and manage Amazon Ads through Adspirer — Sponsored Products, Sponsored Brands, and Sponsored Display, with ASIN targeting, search-term reports, ACoS, and bid optimization. Use for anything on Amazon Advertising or Seller/Vendor Central ads. |
| `adspirer-chatgpt-ads` | Create and manage ChatGPT Ads (OpenAI Ads) through Adspirer — ads that appear inside ChatGPT responses. Use for OpenAI Ads, ChatGPT advertising, chat card ads, or placing ads in ChatGPT. Covers the one-shot launch tool and irreversible archiving. |
| `adspirer-creative` | Write and refresh ad creative with Adspirer — headlines, descriptions, primary text, and ad copy for Google, Meta, TikTok, LinkedIn, and Amazon, plus diagnosing and fixing creative fatigue when CTR falls and frequency rises. Respects each platform's character limits. |
| `adspirer-docs` | Answer questions about Adspirer itself — pricing, plans, quota and tool-call limits, what Adspirer can do, connecting an ad account, supported platforms and AI clients, security, and troubleshooting. Uses the official documentation at adspirer.com/docs rather than guessing. |
| `adspirer-google-ads` | Create and manage Google Ads campaigns through Adspirer — Search, Performance Max, Demand Gen, YouTube, and Display. Use for Google Ads keywords, search terms, quality score, bid strategies, sitelinks and extensions, PMax asset groups, or anything on Google/AdWords. Covers the asset-bundle expiry and ad-group-id traps. |
| `adspirer-launch` | Plan and launch a new ad campaign with Adspirer — start, create, set up, or launch campaigns on one or several platforms, choose which channel fits the goal, and split a budget across channels. Campaigns are created paused and never spend without explicit approval. |
| `adspirer-linkedin-ads` | Create and manage LinkedIn Ads through Adspirer — sponsored content, single image, video, carousel, text ads, and lead-gen forms with B2B job-title, company, and industry targeting. Use for anything on LinkedIn. Every LinkedIn campaign requires a campaign group. |
| `adspirer-mcp` | How to call the Adspirer MCP hub correctly — the router two-step (action "list_tools" then action "execute" with tool_name), the direct tools search_tools and get_tool_schema, per-platform account IDs, quota rules, and the budget unit (every platform takes the account's own currency as a decimal — never cents). Load this before making any Adspirer tool call. |
| `adspirer-meta-ads` | Create and manage Meta Ads (Facebook and Instagram) through Adspirer — image, video, carousel, and lead-gen campaigns, ad sets, audiences, pixels, and creative fatigue. Use for anything on Facebook, Instagram, Meta, or FB ads. Covers the account-currency budget unit (never cents) and the required Facebook page id. |
| `adspirer-optimize` | Find and fix wasted ad spend with Adspirer — cut spend that isn't converting, add negative keywords, exclude audiences and placements, reallocate budget to what works, and check whether campaigns are pacing over or under budget. Proposes changes and asks before spending or moving money. |
| `adspirer-performance-review` | Review ad performance across platforms with Adspirer — how are my ads doing, weekly or monthly reports, a cross-channel scorecard, CPA, ROAS, CTR, spend trends, and auditing whether conversion tracking is set up correctly. Read-only; changes nothing. |
| `adspirer-setup` | Set up your brand workspace — connect to Adspirer, scan brand docs, pull campaign data, and create BRAND.md. Use on first time in a new brand folder, or when the user wants to refresh brand context. |
| `adspirer-tiktok-ads` | Create and manage TikTok Ads through Adspirer — in-feed video, Spark Ads, carousel, app promotion, and conversions campaigns. Use for anything on TikTok. Covers the pixel-placement rule that causes most TikTok failures, the unsupported single-image ad, and per-currency budget floors. |

## Example prompts

- "How did my ad campaigns perform across all platforms over the last 30 days?"
- "Find wasted spend in my Google Ads account and propose fixes for my approval."
- "Plan a Meta campaign for our spring launch with a $50/day budget, and build it paused."

## Safety

- It can change ad accounts, and only with your approval: campaigns are built paused, every change is shown first and read back afterwards.
- **No purchases.** The agent never buys, upgrades, renews or starts a trial of a subscription or
  paid feature for you, including when it runs on its own with browser or payment tools. At a
  quota or plan limit it stops, explains and waits.
- **No unattended changes.** Scheduled or background runs are read-only.
- Sign-in is browser OAuth. Never paste tokens into chat.

An Adspirer account and an applicable plan are required; ad-platform permissions and usage limits
apply.

## Status

Built from https://github.com/Adspirer/adspirer-cursor-plugin v1.0.3 on 2026-11-11. Not yet installed or tested in
Perplexity. Run `node scripts/validate.mjs` after editing.

## Support

- Support: support@adspirer.com
- Documentation: https://www.adspirer.com/docs
- Privacy: https://www.adspirer.com/privacy
- Terms: https://www.adspirer.com/terms
- Security: see [SECURITY.md](SECURITY.md)
