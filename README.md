# Helena for Grok

Give Grok [Helena](https://enrichlabs.ai), the AI marketer for Shopify brands
from Enrich Labs. Helena uses live brand and commerce context to research
opportunities, shape strategy, build campaigns, create on-brand copy and media,
and execute across connected marketing channels.

## What this plugin installs

This plugin installs one remote, Streamable HTTP MCP server:

- Name: `helena`
- Endpoint: `https://agent.enrichlabs.ai/api/mcp`
- Tool: `send_turn`

`send_turn` runs one Helena agent turn and returns final text, a session ID,
the tools Helena called, and any generated media assets. Pass the returned
session ID on later calls to continue the same conversation.

The plugin contains no executable scripts, hooks, downloaded binaries, or
embedded credentials.

## Authentication and access

The first connection uses Enrich Labs OAuth 2.1 with PKCE. Sign in to Enrich
Labs, select a brand, and approve access. Grok handles the resulting OAuth
credentials; no API key is stored in this repository.

MCP access requires an eligible Enrich Labs plan and completed account
onboarding. Each authorization is scoped to the selected Enrich Labs account.

## Data and actions

Requests sent through this plugin go to `agent.enrichlabs.ai`. Helena may read
the brand, product, campaign, and connected marketing data available to the
selected Enrich Labs account. Conversations and generated assets may be stored
in that account's Helena workspace according to the Enrich Labs terms and
privacy policy.

The `send_turn` tool is intentionally marked as potentially destructive because
Helena can use connected services to take real-world actions when the user asks.
Review the proposed action and require explicit approval before publishing
content, changing a storefront or campaign, contacting customers, or spending
money.

## Install from source

```bash
grok plugin install EnrichLabsAI/helena-grok-plugin --trust
```

After installation, authenticate the `helena` MCP server when prompted. You can
inspect its status with:

```bash
grok mcp doctor helena
```

## License

Apache-2.0
