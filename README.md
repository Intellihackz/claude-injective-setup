# injective-claude-starter

query and trade on Injective markets using natural language with Claude Code.

this repo wires up [Claude Code](https://claude.ai/code) with the [Injective MCP server](https://github.com/InjectiveLabs/mcp-server) and [agent-skills](https://github.com/InjectiveLabs/agent-skills) so you can interact with Injective chain — markets, wallets, trades — just by prompting.

---

## quick links

- [tutorial](./tutorial/0-setup.md) - full setup guide
- [examples](./tutorial/1-examples.md) - sample prompts and responses

<br>
<div align="center">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/EEZ8CNdgcVI?si=9prC_VkruCqDXfq3&amp;controls=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>
<br>

---

## stack

- **Claude Code** — AI coding agent (gen AI harness)
- **Injective MCP Server** — connects Claude to Injective chain
- **agent-skills** — `injective-trading-market-data`, `injective-trading-account`, `injective-trading-autosign`

---

## get started

see [tutorial](./tutorial/0-setup.md) for the full setup guide.

```bash
git clone https://github.com/intellihackz/claude-injective-setup
cd claude-injective-setup
```

---

## resources

- [Injective MCP Server](https://github.com/InjectiveLabs/mcp-server)
- [Injective Agent Skills](https://github.com/InjectiveLabs/agent-skills)
- [Injective AI Developers Docs](https://docs.injective.network/developers-ai)
- [Claude Code](https://claude.ai/code)
- [Injective Docs](https://docs.injective.network)
