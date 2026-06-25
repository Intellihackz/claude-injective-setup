# injective-claude-starter

query and trade on Injective markets using natural language with Claude Code.

this repo wires up [Claude Code](https://claude.ai/code) with the [Injective MCP server](https://github.com/InjectiveLabs/mcp-server) and [agent-skills](https://github.com/InjectiveLabs/agent-skills) so you can interact with Injective chain — markets, wallets, trades — just by prompting.

---

## quick links

- [tutorial](./tutorial/0-setup.md) - full setup guide
- [examples](./tutorial/1-examples.md) - sample prompts and responses

<br>
<div align="center">
  <a href="https://www.youtube.com/watch?v=EEZ8CNdgcVI">
    <img src="https://img.youtube.com/vi/EEZ8CNdgcVI/maxresdefault.jpg" width="560" alt="Watch Demo Video" />
  </a>
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
