# Adspirer — Perplexity listing details

| Field | Value |
| --- | --- |
| Name | Adspirer |
| MCP server URL | `https://mcp.adspirer.com/mcp` |
| Transport | Streamable HTTP |
| Sign-in | OAuth 2 in the browser (PKCE); no API key |
| Category | Marketing / Advertising |
| Read-only | No — changes need user approval |
| Logo (1:1) | https://storage.googleapis.com/adspirer-images-v1/brand/adspirer-logo-square.png |
| Website | https://www.adspirer.com |
| Documentation | https://www.adspirer.com/docs |
| Privacy | https://www.adspirer.com/privacy |
| Terms | https://www.adspirer.com/terms |
| Support | support@adspirer.com |

## Short description

AI advertising agent for growing your business. Create, analyze, and optimize ad campaigns across Google, Meta, TikTok, LinkedIn, Amazon, and ChatGPT Ads—with your approval.

## Long description

Adspirer connects Perplexity to your advertising accounts through a hosted MCP server. It covers
Google, Meta, TikTok, LinkedIn, Amazon and ChatGPT Ads. It can change ad accounts, and only with your approval: campaigns are built paused, every change is shown first and read back afterwards. The agent never purchases or upgrades a subscription on your behalf. Sign-in
is browser OAuth with your Adspirer account; ad accounts are connected at
https://adspirer.ai/connections. An Adspirer account and an applicable plan are required.

## Example prompts

- "How did my ad campaigns perform across all platforms over the last 30 days?"
- "Find wasted spend in my Google Ads account and propose fixes for my approval."
- "Plan a Meta campaign for our spring launch with a $50/day budget, and build it paused."

## Getting listed

Perplexity has no self-serve directory for third-party connectors. Users add Adspirer as a
custom connector with the URL above. To ask for it to be offered as a managed connector, email
api@perplexity.ai:

```
Subject: Managed connector request: Adspirer

Hi Perplexity team,

We'd like to request Adspirer as a managed connector.

AI advertising agent for growing your business. Create, analyze, and optimize ad campaigns across Google, Meta, TikTok, LinkedIn, Amazon, and ChatGPT Ads—with your approval.

- MCP server: https://mcp.adspirer.com/mcp (Streamable HTTP, browser OAuth with PKCE)
- Platforms: Google, Meta, TikTok, LinkedIn, Amazon and ChatGPT Ads
- Writes require user approval; campaigns are created paused.
- Logo: https://storage.googleapis.com/adspirer-images-v1/brand/adspirer-logo-square.png
- Website: https://www.adspirer.com
- Docs: https://www.adspirer.com/docs
- Contact: support@adspirer.com

It already works as a custom remote connector in the Perplexity app. Please let us know what
you need from us for review.

Thanks,
Abhi
```
