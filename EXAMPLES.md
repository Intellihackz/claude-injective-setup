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
Here are all 25 active perpetual futures markets on Injective:

|  #  | Ticker                        | Symbol       | Max Leverage | Taker Fee |
|-----|-------------------------------|--------------|--------------|-----------|
| 1   | BTC/USDT PERP                 | BTC          | ~52x         | 0.05%     |
| 2   | BTC/USDC PERP                 | BTC          | ~52x         | 0.05%     |
| 3   | ETH/USDT PERP                 | ETH          | ~52x         | 0.05%     |
| 4   | ETH/USDC PERP                 | ETH          | ~52x         | 0.05%     |
| 5   | INJ/USDT PERP                 | INJ          | ~30x         | 0.05%     |
| 6   | INJ/USDC PERP                 | INJ          | ~30x         | 0.05%     |
| 7   | SOL/USDT PERP                 | SOL          | ~30x         | 0.05%     |
| 8   | ARB/USDT PERP                 | ARB          | ~12x         | 0.05%     |
| 9   | ATOM/USDT PERP                | ATOM         | ~10.5x       | 0.05%     |
| 10  | TIA/USDT PERP                 | TIA          | ~5.5x        | 0.05%     |
| 11  | LINK/USDC PERP                | LINK         | ~12x         | 0.05%     |
| 12  | PEPE/USDT PERP                | PEPE         | ~10.5x       | 0.05%     |
| 13  | 1000PEPE/USDT PERP            | 1000PEPE     | ~5.1x        | 0.30%     |
| 14  | 1MPEPE/USDT PERP              | 1MPEPE       | ~5.1x        | 0.10%     |
| 15  | 1MPEPE/USDT                   | 1MPEPE       | ~5.1x        | 0.30%     |
| 16  | XAU/USDT PERP                 | XAU (Gold)   | ~52x         | 0.05%     |
| 17  | XAG/USDT PERP                 | XAG (Silver) | ~52x         | 0.05%     |
| 18  | GOLD/USDT PERP                | GOLD         | ~5.1x        | 0.10%     |
| 19  | EUR/USDT PERP                 | EUR          | ~101x        | 0.05%     |
| 20  | GBP/USDT PERP                 | GBP          | ~101x        | 0.05%     |
| 21  | JPY/USDT PERP                 | JPY          | ~5.1x        | 0.30%     |
| 22  | TIA/USDT-01NOV2023            | TIA          | ~20x         | 0.10%     |
| 23  | TRUCPI/USDT PERP              | TRUCPI       | ~5.1x        | 0.10%     |
| 24  | EVINDEX/USDT PERP             | EVINDEX      | ~5.1x        | 0.10%     |
| 25  | CANELO-DEF-CRAWFORD/USDT PERP | Sports Bet   | ~1x          | 0.20%     |

Oracle types used: Pyth, Chainlink Data Streams, and Provider/Pricefeed.
```

> note: this output is from testnet — mainnet has more markets (63+).

---

## 2. get current price

**prompt:**
```
what is the current price of INJ?
```

**output:**
```
The current oracle price of INJ is $2.864608 USDT.
```

> note: price is fetched live from the oracle — your result will differ.

---

## 3. generate a new wallet

**prompt:**
```
generate a new Injective wallet
```

Claude will ask for a password to encrypt the wallet keystore:

```
I need a password to encrypt the wallet keystore. Please provide one via the prompt
(it will be used to secure your wallet — never share it).

What password would you like to use? (min 8 characters)
```

**output:**
```
Your new Injective wallet has been generated:

Address: inj1n69ekj3f5qe6aqmfet0m94lcmtpkrplsnlxjv9

Mnemonic (seed phrase):
team polar brain fever accident crush dash jar satisfy front crane auto

CRITICAL: Write down your mnemonic phrase immediately and store it somewhere safe
and offline. It will never be shown again. Anyone with this phrase can access your funds.
```

---

## 4. check wallet balance

**prompt:**
```
show balances for inj1jthfhpz9m54cmzg2rdzz257k7744ec8nycz702
```

**output:**
```
Balances for inj1jthfhpz9m54cmzg2rdzz257k7744ec8nycz702:

Bank Balances

| Token | Amount     | Type   |
|-------|------------|--------|
| INJ   | 989.999970 | Native |

Subaccount Balances: None
```

---

## 5. send tokens

**prompt:**
```
send 10 INJ to inj1n69ekj3f5qe6aqmfet0m94lcmtpkrplsnlxjv9
```

Claude confirms before sending:

```
Before proceeding, please confirm this transaction:

- From: inj1jthfhpz9m54cmzg2rdzz257k7744ec8nycz702
- To: inj1n69ekj3f5qe6aqmfet0m94lcmtpkrplsnlxjv9
- Amount: 10 INJ

Do you want to proceed?
```

then asks for your wallet password to sign:

```
I need the keystore password for the sender wallet to sign the transaction. What is the password?
```

**output:**
```
Transaction successful!

- Tx Hash: 1A659E9C9C1C7C33282AF8E5FB900BE29E5795B2B84929AB22FCB49F7B70FE59
- From: inj1jthfhpz9m54cmzg2rdzz257k7744ec8nycz702
- To: inj1n69ekj3f5qe6aqmfet0m94lcmtpkrplsnlxjv9
- Amount: 10 INJ
```

---

## notes

- all market data queries are live — results will differ from the above depending on when you run them
- wallet address and mnemonic above are from a testnet session — do not send real funds to this address

---

## 6. get testnet INJ

**prompt:**
```
show me how to obtain testnet INJ in my wallet
```

**output:**
```
To get testnet INJ, use the Injective Testnet Faucet:

Steps

1. Go to the faucet:
   Visit https://testnet.faucet.injective.network

2. Enter your wallet address:
   Paste your address: inj1n69ekj3f5qe6aqmfet0m94lcmtpkrplsnlxjv9

3. Request tokens:
   Click "Get INJ" — the faucet typically sends 100 testnet INJ.

4. Verify your balance:
   After a few seconds, you can check using:
   "show balances for inj1n69ekj3f5qe6aqmfet0m94lcmtpkrplsnlxjv9"

---

Alternative: CLI Faucet

curl -X POST https://testnet.faucet.injective.network/api/faucet \
  -H "Content-Type: application/json" \
  -d '{"address": "inj1n69ekj3f5qe6aqmfet0m94lcmtpkrplsnlxjv9"}'

Note: Testnet INJ has no real value — it's only for testing on Injective's
Testnet network (injective-888).
```

---

## 7. check portfolio value

**prompt:**
```
what is my total portfolio value?
```

**output:**
```
Here's the portfolio summary for inj1jthfhpz9m54cmzg2rdzz257k7744ec8nycz702:

| Asset | Amount     | Price   | Value (USD) |
|-------|------------|---------|-------------|
| INJ   | 979.999943 | $2.8737 | $2,816.22   |

Total Portfolio Value: ~$2,816.22 USDT

Note: Balance dropped from ~990 to ~980 INJ after the 10 INJ transfer sent
earlier (small gas fees account for the ~0.000057 difference).
```

---

## 8. bridge withdraw to Ethereum

**prompt:**
```
can you bridge withdraw to eth
```

Claude asks for details:

```
I need a few details to proceed with the Peggy bridge withdrawal:

1. How much INJ do you want to withdraw?
2. Your Ethereum address (0x...) to receive the funds?

Note: This uses the Peggy bridge — takes ~30 min to arrive on Ethereum
and cannot be reversed once submitted. A small bridge fee applies.
```

user responds with amount and ETH address, Claude confirms:

```
Please confirm this bridge withdrawal:

- From: inj1jthfhpz9m54cmzg2rdzz257k7744ec8nycz702
- To (Ethereum): 0xEE064E6898ED9D06bfBE083B2E91328272A190f6
- Amount: 50 INJ
- Bridge: Peggy (~30 min, irreversible)

Do you want to proceed?
```

after confirming and entering wallet password:

**output:**
```
Bridge withdrawal submitted successfully!

- Tx Hash: DFD37A2717353F1FD9490AF86E25B8C662ACD8F32495998F547D8BE699EA74C0
- From: inj1jthfhpz9m54cmzg2rdzz257k7744ec8nycz702
- To (ETH): 0xEE064E6898ED9D06bfBE083B2E91328272A190f6
- Amount: 50 INJ
- Bridge Fee: 0.001 INJ
- Estimated Arrival: ~30 minutes

You can track it on the Injective Bridge explorer at https://bridge.injective.network.
```

---

## 9. open a perpetual position

**prompt:**
```
open a market order long position for inj/usdt of 100$ with 5x leverage
```

Claude asks for your wallet password to sign, then:

**output:**

```
Position opened successfully!

| Field             | Value                                                            |
|-------------------|------------------------------------------------------------------|
| Tx Hash           | 7B8266B6F83BC7712211C16748BD78C21CABB83CFA7EEB6878AB56C139718A1B |
| Execution Price   | $2.786 USDT                                                      |
| Quantity          | 35.89 INJ                                                        |
| Margin Used       | $21.00 USDT                                                      |
| Liquidation Price | $2.2845 USDT                                                     |
```
