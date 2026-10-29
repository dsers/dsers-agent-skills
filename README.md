# DSers Dropshipping Skill

The official DSers Agent Skill for dropshippers. It works in AI apps that support Agent Skills, such as Claude, Codex, Cursor, OpenClaw, Hermes Agent, and Gemini CLI, and helps with the problems that cost a dropship store money:

| Job | What it helps with |
|---|---|
| Profit check | Whether each product makes money after payment fees, ads, refunds, and duties; where the money goes; prices and pricing rules |
| Supplier and order problems | Items out of stock after the customer paid, supplier cancellations, late or lost parcels, wrong or damaged items, returns, PayPal and card disputes, customer messages, and choosing suppliers |
| Listing cleanup | Turning imported supplier products into store-ready titles, descriptions, variants, size charts, and SEO fields, one at a time or as a Shopify CSV |
| Pre-launch check | Policies, prices, product pages, and products checked against payment, Google, ad, and US, EU, and UK consumer rules |

Laws, platform rules, and fees the skill relies on are listed with their official sources in [`references/rules.md`](skills/dsers-dropshipping/references/rules.md), with the date they were checked.

The skill works without a DSers account, using the details you give it. Connect [DSers MCP](#dsers-mcp), the official MCP server from DSers for AI-powered dropshipping automation, to move from product discovery to listings, store operations, orders, fulfillment, and delivery tracking — all in one conversation. Changes to your DSers account are saved only after you confirm each one.

## Install

**Claude Code**

```text
/plugin marketplace add dsers/dsers-agent-skills
/plugin install dsers-dropshipping@dsers-agent-skills
```

**Claude (web and desktop)**: zip the folder `skills/dsers-dropshipping` (the folder itself, not the files inside it) and upload the ZIP under Customize → Skills.

**Codex, Cursor, OpenClaw, Hermes Agent, and other Agent Skills apps**

```bash
npx skills add dsers/dsers-agent-skills
```

Choose your app when asked.

**Hermes Agent** can also install it directly:

```bash
hermes skills install dsers/dsers-agent-skills/skills/dsers-dropshipping
```

**Gemini CLI**

```bash
gemini extensions install https://github.com/dsers/dsers-agent-skills
```

## Try it

- "I have about 120 orders a month but my bank balance isn't growing. Am I making money?"
- "A customer paid three days ago and the supplier says the item is out of stock. What should I do?"
- "A customer opened a PayPal dispute saying they never got the item, but tracking says delivered."
- "Clean up this AliExpress title and these variants for my Shopify store."
- "My store sells to the US and Europe. What should I check before running ads?"

## About DSers

DSers is an ecommerce platform founded in 2018 that helps sellers spend less time on repetitive operations and more time building their business — supporting dropshipping and wholesale through connected sourcing, automation, and fulfillment workflows. As an official Alibaba Group partner, DSers supports 10M+ dropshippers, with 100M+ SKUs in the product pool and 300M+ orders processed. DSers supports sourcing across AliExpress, 1688.com, Alibaba.com, and the DSers Agent Network, giving sellers transparent options as their sourcing needs evolve.

Technology should understand more, automate more, and stay dependable—so people can focus on judgment, creativity, relationships, and growth. [More about DSers](https://www.dsers.com/en/about-us)

## DSers MCP

DSers MCP is the official MCP server from DSers for AI-powered dropshipping automation. Connect your favorite AI client to DSers and move from product discovery to listings, store operations, orders, fulfillment, and delivery tracking — all in one conversation.

What you can do with DSers MCP:

- **Discover products and logistics**: Search by keyword or image, inspect supplier products, compare logistics by country, and monitor supplier-product changes.
- **Build and optimize import drafts**: Create import-list products, then edit content, images, options, variants, prices, organization, and categories before launch.
- **Configure stores and publish**: Connect or reauthorize stores, create Shopify shipping profiles, resolve logistics choices, and publish through tracked jobs.
- **Operate catalogs and mappings**: Inspect live products, update price or stock, import store products, and manage Basic, Advanced, or AI-assisted supplier mappings.
- **Run orders and supplier fulfillment**: Validate addresses, update order details, and place or cancel supplier orders.
- **Control tracking and buyer updates**: Inspect package events, refresh supplier tracking, synchronize or replace store tracking numbers, and send buyer notifications.

DSers MCP works alongside the DSers dashboard.

## Connect DSers MCP

You need:

- A DSers account. [Sign up](https://accounts.dsers.com/accounts/register?utm_source=agent_skills&utm_medium=ai_assistant&utm_campaign=dsers_dropshipping&utm_content=readme)
- A DSers Advanced, Pro, or Enterprise plan. These plans include MCP Connection; Basic does not ([DSers MCP documentation](https://www.dsers.com/en/mcp-server), [DSers pricing page](https://www.dsers.com/pricing)).
- At least one Shopify or Wix store connected in DSers.

Then add the DSers MCP server `https://ai.dsers.com/mcp` to your AI app and sign in to DSers in the browser window that opens. Do not paste passwords, API keys, or tokens into your app's configuration.

**Claude Code**: if you installed the plugin above, it adds the server for you; run `/mcp`, select the DSers server, and sign in. Otherwise:

```bash
claude mcp add --transport http --scope user dsers https://ai.dsers.com/mcp
```

```bash
claude mcp login dsers
```

**Claude (web and desktop)**: open [DSers in the Claude directory](https://claude.ai/directory/dsers), or go to Customize → Connectors and search for DSers. Add it and sign in to DSers. On Team and Enterprise plans, an owner adds DSers for the organization first.

**Codex CLI**

```bash
codex mcp add dsers --url https://ai.dsers.com/mcp
```

```bash
codex mcp login dsers
```

**Cursor**: add the server to `~/.cursor/mcp.json`, then sign in when Cursor asks.

```json
{
  "mcpServers": {
    "dsers": { "url": "https://ai.dsers.com/mcp" }
  }
}
```

**Gemini CLI**: add the server to `~/.gemini/settings.json`, then run `/mcp auth dsers`.

```json
{
  "mcpServers": {
    "dsers": { "httpUrl": "https://ai.dsers.com/mcp" }
  }
}
```

**OpenClaw**

```bash
openclaw mcp set dsers '{"url":"https://ai.dsers.com/mcp","transport":"streamable-http","auth":"oauth"}'
```

```bash
openclaw mcp login dsers
```

**Hermes Agent**: add the server to the active profile's `config.yaml` (normally `~/.hermes/config.yaml`), keeping the other entries. The [DSers plugin for Hermes](https://github.com/dsers/dsers-agent-plugin/tree/main/plugins/hermes) uses the same entry. Sign in from a separate terminal, then run `/reload-mcp` in the Hermes session. Run the same sign-in command again when the sign-in expires.

```yaml
mcp_servers:
  dsers:
    url: https://ai.dsers.com/mcp
    auth: oauth
    trust: untrusted
    strict_redirect_headers: true
```

```bash
hermes mcp login dsers
```

More details are in the [DSers MCP documentation](https://www.dsers.com/en/mcp-server).

## Privacy

The skill contains instructions only. It does not collect, store, or send data itself. When DSers is connected, your AI app sends requests to the DSers MCP server under your DSers sign-in, and DSers processes that data under its own terms.

- DSers privacy policy: https://www.dsers.com/en/privacy

## Support

- Questions about this skill: [GitHub Issues](https://github.com/dsers/dsers-agent-skills/issues)
- DSers account, plan, and DSers MCP questions: [DSers Help Center](https://help.dsers.com/) or support@dserspro.com

## License

[MIT-0](LICENSE)
