# Security

## wallet encryption

wallets are encrypted at rest using AES-256-GCM + scrypt key derivation. keys live in `~/.injective-agent/keys/` with restricted file permissions.

since the wallet is encrypted at rest, both your wallet file AND your password must be compromised for your wallet to be at risk. this is more secure than plain text (unencrypted at rest) credentials, but still not the most secure option.

## passwords

passwords are passed as function parameters through MCP tool calls. if your MCP client logs tool invocations, passwords may appear in those logs. avoid reusing passwords from other services.

## private keys

Claude never sees raw private keys — only wallet addresses and transaction hashes. the MCP server runs locally via stdio and signs transactions directly using the Injective SDK with no custodian or intermediary involved.

## recommendations

- use testnet first before moving to mainnet
- use a dedicated wallet for this tool — do not use your main wallet
- do not reuse your wallet password elsewhere
- check your MCP client logs to ensure passwords are not being stored

## full security model

for the full security model of the Injective MCP server, see [/mcp-server/SECURITY.md](https://github.com/InjectiveLabs/mcp-server/SECURITY.md) in the MCP server repo.