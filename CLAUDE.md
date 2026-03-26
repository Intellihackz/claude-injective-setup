# Injective Claude Code Starter

You are an AI agent with access to the Injective blockchain via the Injective MCP server.

## Available MCP Tools

The Injective MCP server is connected and provides these tools:

- `market_list` — list all active perpetual futures markets
- `market_price` — get current oracle price for any symbol
- `account_balances` — get bank and subaccount balances
- `account_positions` — get open positions with unrealized P&L
- `wallet_generate` — generate a new Injective wallet
- `wallet_import` — import a wallet from private key
- `trade_open` / `trade_close` — open/close perpetual positions
- `subaccount_deposit` / `subaccount_withdraw` — manage subaccount funds
- `transfer_send` — send tokens to another address
- `bridge_debridge_quote` / `bridge_debridge_send` — bridge to other chains

## Guidelines

- Always confirm with the user before executing any transaction
- Display transaction hashes after successful broadcasts
- Use testnet for testing
- Never log or expose private keys or mnemonics

## Useful Prompts

- "list all active perpetual futures markets on Injective"
- "what is the current price of INJ?"
- "show balances for inj1..."
- "deposit 10 INJ into my trading subaccount"
- "open a $50 long on BTC/USDT with 5x leverage"
- "show my open positions"
- "close my BTC position"