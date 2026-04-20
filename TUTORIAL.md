# claude-injective-setup — tutorial

query and trade on Injective markets using natural language with Claude Code.

this tutorial walks through setting up Claude Code with the Injective MCP server and agent-skills so you can list markets, check prices, manage wallets, and execute trades — just by prompting.

---

## what you can do

- list all active perpetual futures markets
- get live prices for any asset
- generate and manage Injective wallets
- check wallet and subaccount balances
- send tokens to any Injective address
- deposit into a trading subaccount
- open and close perpetual positions
- bridge tokens to other chains via deBridge

---

## prerequisites

- Node.js v22+
- a Claude Pro or Max subscription
- Claude Code — install with:

**windows:**
```
irm https://claude.ai/install.ps1 | iex
```

**mac/linux:**
```bash
npm install -g @anthropic-ai/claude-code
```

---

## setup

### 1. fork and clone this repo

first, fork this repo on GitHub, then clone your fork:

```bash
git clone https://github.com/intellihackz/claude-injective-setup
cd claude-injective-setup
```

### 2. clone and build the Injective MCP server

```bash
git clone https://github.com/InjectiveLabs/mcp-server
cd mcp-server
npm install --ignore-scripts
npm run build
cd ..
```

> **windows note:** if `npm install` fails with an EBUSY error, use `npm install --ignore-scripts`

### 3. register the MCP server with Claude Code

**mac/linux:**
```bash
claude mcp add -e INJECTIVE_NETWORK=testnet injective node ~/mcp-server/dist/mcp/server.js
```

this will add the following to your `~/.claude.json`:

```json
{
  "mcpServers": {
    "injective": {
      "command": "node",
      "args": ["/home/YOUR_USERNAME/mcp-server/dist/mcp/server.js"],
      "env": {
        "INJECTIVE_NETWORK": "testnet"
      }
    }
  }
}
```

**windows:**
```bash
claude mcp add injective node C:\path\to\mcp-server\dist\mcp\server.js
```

to set the network on windows, open `~/.claude.json` and add the env block manually:

```json
{
  "mcpServers": {
    "injective": {
      "command": "node",
      "args": ["C:\\path\\to\\mcp-server\\dist\\mcp\\server.js"],
      "env": {
        "INJECTIVE_NETWORK": "testnet"
      }
    }
  }
}
```

verify the server is connected:

```bash
claude mcp list
```

you should see: `injective: node ... - ✓ Connected`

### 4. install agent-skills

```bash
npx skills add InjectiveLabs/agent-skills --skill injective-trading-market-data injective-trading-account injective-trading-autosign
```

### 5. start Claude Code

```bash
claude
```

---

## wallet setup

generate a new wallet inside Claude Code:

```
generate a new Injective wallet
```

> ⚠️ save your mnemonic — it's shown only once.

to get testnet INJ, prompt Claude Code:

```
show me how to obtain testnet INJ in my wallet
```

---

## example prompts

try these to get started:

```
list all active perpetual futures markets on Injective
```

```
what is the current price of INJ?
```

```
deposit 10 INJ into my trading subaccount
```

see [EXAMPLES.md](./EXAMPLES.md) for more prompts and their full responses.

---

## security

- private keys are encrypted at rest with AES-256-GCM + scrypt
- keys live in `~/.injective-agent/keys/` with restricted permissions
- Claude never sees raw private keys — only addresses and tx hashes
- since the wallet is encrypted at rest, both your wallet file AND password must be compromised for your wallet to be at risk — this is more secure than plaintext credentials, but still not the most secure option
- passwords are passed as function parameters through MCP tool calls — if your MCP client logs tool invocations, passwords may appear in those logs

---

## networks

| network | value |
|---------|-------|
| mainnet | `mainnet` |
| testnet | `testnet` |

---

## resources

- [Injective MCP Server](https://github.com/InjectiveLabs/mcp-server)
- [Injective Agent Skills](https://github.com/InjectiveLabs/agent-skills)
- [Injective AI Developers Docs](https://docs.injective.network/developers-ai)
- [Claude Code](https://claude.ai/code)
- [Injective Docs](https://docs.injective.network)
