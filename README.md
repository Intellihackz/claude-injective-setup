# injective-claude-starter

query and trade on Injective markets using natural language with Claude Code.

this starter repo wires up Claude Code with the Injective MCP server and agent-skills so you can list markets, check prices, manage wallets, and execute trades — just by prompting.

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

- Node.js v18+
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

### 1. clone this repo

```bash
git clone https://github.com/YOUR_USERNAME/injective-claude-starter
cd injective-claude-starter
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

**windows:**
```bash
claude mcp add injective node C:\path\to\mcp-server\dist\mcp\server.js
```

to set the network on windows, open `~/.claude.json` and add the env block:

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
npx skills add InjectiveLabs/agent-skills
```

when prompted, select:
- `injective-trading-market-data`
- `injective-trading-account`
- `injective-trading-autosign`

`npx skills add` installs the skills to both `.agents/skills/` and `.claude/skills/` automatically.

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

get testnet INJ: https://testnet.faucet.injective.network/

---

## example prompts

### market data

```
list all active perpetual futures markets on Injective
```

```
what is the current price of INJ?
```

```
what is the BTC/USDT perp funding rate?
```

### account

```
show balances for inj1...
```

```
send 10 INJ to inj1...
```

### trading

```
deposit 10 INJ into my trading subaccount
```

```
open a $50 long on BTC/USDT with 5x leverage
```

```
show my open positions
```

```
close my BTC position
```

### limit orders

```
open a limit buy on ETH at $3200 for $100 notional, 3x leverage
```

```
list my open limit orders
```

```
cancel order 0xabc...
```

### bridging

```
get a deBridge quote to bridge 50 USDT from Injective to Base
```

---

## security

- private keys are encrypted at rest with AES-256-GCM + scrypt
- keys live in `~/.injective-agent/keys/` with restricted permissions
- Claude never sees raw private keys — only addresses and tx hashes
- see [SECURITY.md](https://github.com/InjectiveLabs/mcp-server/blob/main/SECURITY.md) for the full security model

---

## networks

| network | value |
|---------|-------|
| mainnet | `mainnet` |
| testnet | `testnet` |

testnet faucet: https://testnet.faucet.injective.network/

---

## resources

- [Injective MCP Server](https://github.com/InjectiveLabs/mcp-server)
- [Injective Agent Skills](https://github.com/InjectiveLabs/agent-skills)
- [Claude Code](https://claude.ai/code)
- [Injective Docs](https://docs.injective.network)