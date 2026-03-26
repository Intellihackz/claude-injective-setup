# Example Session

real prompts and outputs from a Claude Code session with the Injective MCP server.

---

## 1. list all active perpetual futures markets

**prompt:**
```
list all active perpetual futures markets on Injective
```

**output:**

```
Here are all 63 active perpetual futures markets on Injective (Mainnet):

Crypto — Major

| Symbol | Ticker         | Max Leverage | Taker Fee |
|--------|----------------|--------------|-----------|
| BTC    | BTC/USDT PERP  | ~52x         | 0.05%     |
| ETH    | ETH/USDT PERP  | ~52x         | 0.05%     |
| SOL    | SOL/USDT PERP  | ~30x         | 0.05%     |
| BNB    | BNB/USDT PERP  | ~30x         | 0.05%     |
| INJ    | INJ/USDT PERP  | ~30x         | 0.05%     |
| XRP    | XRP/USDT PERP  | ~30x         | 0.05%     |
| DOGE   | DOGE/USDT PERP | ~12x         | 0.05%     |
| AVAX   | AVAX/USDT PERP | ~12x         | 0.05%     |
| LINK   | LINK/USDT PERP | ~12x         | 0.05%     |
| LTC    | LTC/USDT PERP  | ~30x         | 0.05%     |

Crypto — Mid/Alt

| Symbol  | Ticker          | Max Leverage |
|---------|-----------------|--------------|
| ATOM    | ATOM/USDT PERP  | ~10x         |
| SUI     | SUI/USDT PERP   | ~12x         |
| APT     | APT/USDT PERP   | ~30x         |
| ARB     | ARB/USDT PERP   | ~12x         |
| TRUMP   | TRUMP/USDT PERP | ~5.5x        |
| HYPE    | HYPE/USDT PERP  | ~10x         |
| BERA    | BERA/USDT PERP  | ~12x         |
| PEPE    | PEPE/USDT PERP  | ~10x         |
| ...and more

Commodities & Forex

| Symbol | Ticker          | Max Leverage |
|--------|-----------------|--------------|
| XAU    | XAU/USDT PERP   | ~52x         |
| XAG    | XAG/USDT PERP   | ~52x         |
| EUR    | EUR/USDT PERP   | ~101x        |
| GBP    | GBP/USDT PERP   | ~101x        |
| USOIL  | USOIL/USDT PERP | ~30x         |

US Equities (TradFi)

| Symbol | Ticker          | Max Leverage |
|--------|-----------------|--------------|
| NVDA   | NVDA/USDT PERP  | ~30x         |
| TSLA   | TSLA/USDT PERP  | ~30x         |
| AAPL   | AAPL/USDT PERP  | ~30x         |
| MSFT   | MSFT/USDT PERP  | ~30x         |
| AMZN   | AMZN/USDT PERP  | ~30x         |
| GOOGL  | GOOGL/USDT PERP | ~30x         |
| META   | META/USDT PERP  | ~12x         |
| MSTR   | MSTR/USDT PERP  | ~30x         |
| COIN   | COIN/USDT PERP  | ~30x         |

Private Companies

| Symbol    | Ticker              | Max Leverage |
|-----------|---------------------|--------------|
| ANTHROPIC | ANTHROPIC/USDT PERP | ~5.5x        |
| SPACEX    | SPACEX/USDT PERP    | ~5.5x        |

63 total active markets. All use a 0.05% taker fee.
```

---

## 2. get current price

**prompt:**
```
what is the current price of INJ?
```

**output:**
```
The current oracle price of INJ is $X.XX USD (fetched live from Pyth oracle on Injective mainnet).
```

---

## 3. generate a new wallet

**prompt:**
```
generate a new Injective wallet
```

**output:**
```
New Injective wallet generated:

Address:  inj1jthfhpz9m54cmzg2rdzz257k7744ec8nycz702
Mnemonic: goose already hurdle afraid dad couch february hobby damp course vessel wash

⚠️ Write down your mnemonic now — it will not be shown again.
```

---

## 4. check wallet balance

**prompt:**
```
show balances for inj1jthfhpz9m54cmzg2rdzz257k7744ec8nycz702
```

**output:**
```
Balances for inj1jthfhpz9m54cmzg2rdzz257k7744ec8nycz702

| Token | Type   | Balance      |
|-------|--------|--------------|
| INJ   | Native | 1,000.000000 |

Subaccount: No positions or deposits.
```

---

## 5. send tokens

**prompt:**
```
send 10 INJ to inj1abc...xyz
```

**output:**
```
Sending 10 INJ to inj1abc...xyz

Transaction broadcast successfully.
TX Hash: 0xabc123...
```

---
