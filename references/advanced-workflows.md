# TTTracker - Advanced Workflows

## 1. Full Single Token Analysis
1. Resolve token name → address if needed
2. Call Token Fees endpoint (days=30)
3. Fetch market data (mcap, volume, holders) from available tools
4. Calculate:
   - Claimable USD value
   - Lifetime USD value
   - Average daily earnings
   - Best day performance
5. Render full TTTracker Dashboard
6. Offer: Claim / Compare / Set Alert / Historical deeper look

## 2. Portfolio Mode (My Fees)
- Detect user wallet
- Call creator-fees endpoint
- Show total claimable + lifetime across all tokens
- List top 5 tokens by claimable fees
- Allow drilling into any single token

## 3. Ranking Engine
- Maintain awareness of top Bankr agents (Surplus, CLAWD, gitlawb, aeon, etc.)
- Rank by:
  - Weekly revenue
  - Lifetime fees
  - Market Cap
  - 24h Volume
- Display clean ranked table

## 4. Comparison Mode
When user asks to compare 2+ tokens:
- Fetch fees + market data for each
- Show side-by-side metrics
- Highlight winner on: Fees, Volume, Growth, Holders

## 5. Smart Alerts & Suggestions
Always evaluate:
- If claimableWeth ≥ 0.01 → “Recommended to claim now”
- If daily average rising → “Strong momentum”
- If volume high but claimable low → “Fees may have been claimed recently”

## 6. Historical Deep Dive
- Show last 7 days detailed
- Show best day ever
- Calculate 7d vs 30d trend (up/down %)
