# TTTracker - Advanced API Reference

## 1. Token Fees (Primary Endpoint)
**GET** `https://api.bankr.bot/token-launches/{tokenAddress}/fees?days=30`

Legacy (masih bekerja):  
`https://api.bankr.bot/public/doppler/token-fees/{tokenAddress}?days=30`

### Important Response Fields
- `lifetimeEarnedWeth` → Total lifetime fees in WETH
- `totals.claimableWeth` → Fees that can be claimed right now
- `totals.claimedWeth` → Already claimed
- `dailyEarnings[]` → Array of `{ date, weth }`
- `lifetimeBestDay` → Best earning day
- `tokens[0].claimable` → Detailed claimable (token0 = WETH, token1 = token)
- `tokens[0].share` → Creator share percentage (usually 57%)

### Example Response Structure
```json
{
  "address": "0x...",
  "chain": "base",
  "days": 30,
  "lifetimeEarnedWeth": "1.2345",
  "lifetimeDays": 42,
  "lifetimeBestDay": { "date": "2026-03-22", "weth": "0.0891" },
  "dailyEarnings": [
    { "date": "2026-08-10", "weth": "0.0123" },
    { "date": "2026-08-11", "weth": "0.0087" }
  ],
  "totals": {
    "claimableWeth": "0.0456",
    "claimedWeth": "1.1889",
    "claimCount": 5
  },
  "tokens": [
    {
      "tokenAddress": "0x...",
      "name": "Example",
      "symbol": "EXM",
      "share": "57.00%",
      "claimable": { "token0": "0.0456", "token1": "12345.67" },
      "claimed": { "token0": "1.1889", "token1": "500000", "count": 5 }
    }
  ]
}
```

## 2. Creator / Wallet Level Fees
**GET** `https://api.bankr.bot/public/doppler/creator-fees/{walletAddress}?days=30`

Returns the same structure but aggregated across **all tokens** created by that wallet.

## 3. Claimable Check (Lightweight)
**GET** `https://api.bankr.bot/public/doppler/claimable-fees/{tokenAddress}?beneficiary={walletAddress}`

Useful for quick “can claim?” checks.

## 4. Recent Launches
**GET** `https://api.bankr.bot/token-launches`  
Returns the 50 most recent Bankr token launches.

## 5. Agent Profiles
**GET** `https://api.bankr.bot/agent-profiles/{slug-or-address}`

Contains marketCapUsd and weeklyRevenueWeth (auto-updated).

## Best Practices for TTTracker
- Always request `days=30` by default (max 90)
- Convert WETH → USD using current ETH price
- Cache results for 1-2 minutes in conversation
- Prefer `token-launches/.../fees` over the legacy endpoint
- If claimableWeth > 0.005 → strongly suggest claiming
```
