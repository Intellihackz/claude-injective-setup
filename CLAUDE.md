# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an **Agent Skills bundle** for interacting with the Injective decentralized derivatives exchange. It is not a traditional software project — there is no build system, source code, or test suite. Instead, it is a collection of **Agent Skill definitions** (`.agents/skills/`) that teach Claude Code how to use Injective's MCP (Model Context Protocol) server to perform on-chain operations.

## Skill Activation

Skills in `.agents/skills/` auto-activate based on prompt context. When users ask about trading, balances, or market data, Claude reads the relevant `SKILL.md` files and calls the corresponding MCP tools (`mcp__injective__*`). The MCP server must be running for tool calls to succeed.

## MCP Server Setup

The MCP server is a prerequisite for all Injective tool calls:

```bash
git clone https://github.com/InjectiveLabs/mcp-server injective-mcp-server
cd injective-mcp-server
npm install && npm run build
```

Configure in `~/.claude/mcp.json`:
```json
{
  "mcpServers": {
    "injective": {
      "command": "node",
      "args": ["/absolute/path/to/injective-mcp-server/dist/mcp/server.js"],
      "env": { "INJECTIVE_NETWORK": "mainnet" }
    }
  }
}
```

To install or update skills:
```bash
npx skills add InjectiveLabs/agent-skills --skill injective-mcp-servers
```

## Architecture

### Skill Dependency Graph

```
injective-mcp-servers  (base — provides all MCP tools)
    ├── injective-trading-account     (read-only: balances, positions)
    ├── injective-trading-autosign    (AuthZ delegation for session trading)
    └── injective-trading-market-data (real-time market prices and metadata)
```

### Key Concepts

**Bank balance ≠ Subaccount balance**: Funds must be deposited via `subaccount_deposit` (wraps `MsgDeposit`) before placing derivative orders. Querying `account_balances` alone does not show trading margin.

**Denom formats** (4 types):
- Native: `inj`
- Peggy (bridged ERC-20): `peggy0x...` (USDT = `peggy0xdac17f958d2ee523a2206206994597c13d831ec7`)
- IBC: `ibc/HASH`
- EVM ERC-20: `erc20:0x...`

**EIP-712 signing** (MetaMask path): Always use V2 (`getEip712TypedDataV2` + `SIGN_EIP712_V2`). V1 produces invalid signatures. The `evmChainId` must match MetaMask's connected chain, and fee objects must be identical between `getEip712TypedDataV2()` and `createTransaction()`.

**SDK version pinning**: `@injectivelabs/sdk-ts` must be pinned to exactly `v1.17.8`. v1.18+ breaks EIP-712 compatibility.

**Margin calculation**: Add 1–2% buffer above the exact minimum margin to avoid rounding rejections. Validate against `max(oraclePrice, markPrice)`, not oracle price alone.

**AuthZ expiry**: Default safe expiry is 24h (86400s). The maximum recommended is 72h (259200s). Scoped to trading message types only — no withdrawals, transfers, or governance.

**Market order slippage**: Use 1% slippage for market closes (not 5%).

**Reduce-only orders**: Pass `margin: '0'` to signal reduce-only intent.

**Tick sizes**: `minPriceTickSize` from the indexer is in chain format — divide by 10^6 for the human-readable value. `minQuantityTickSize` is already in human format.
