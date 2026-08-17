# TTTracker - Usage Examples & Expected Behavior

## 1. Basic Single Token Dashboard

**User:**
Show TTTracker dashboard for CLAWD

**Expected Behavior:**
- Resolve CLAWD token address
- Fetch fees data (days=30)
- Fetch market data if available
- Render full dashboard with:
  - Market Cap, Volume, Holders
  - Claimable Fees + Lifetime Fees (WETH + USD)
  - Weekly revenue
  - Daily earnings (last 7–14 days)
  - Quick Actions (Claim, Compare, Alert)

---

## 2. My Portfolio / Creator View

**User:**
My fee dashboard  
atau  
Show my TTTracker  
atau  
How much fees have I earned?

**Expected Behavior:**
- Detect user’s wallet
- Call creator-fees endpoint
- Show total claimable + lifetime across all tokens
- List top performing tokens owned by the user
- Allow drilling down into any single token

---

## 3. Top Agents Ranking

**User:**
Top Bankr agents by revenue  
atau  
TTTracker ranking  
atau  
Show top agents

**Expected Behavior:**
- Display ranked table (Top 10)
- Columns: Rank | Name | Market Cap | Weekly Fees | 24h Volume
- Sort by weekly revenue by default
- Offer to switch sorting (by mcap / lifetime fees / volume)

---

## 4. Comparison Mode

**User:**
Compare CLAWD vs Surplus  
atau  
TTTracker compare 0xabc... and 0xdef...

**Expected Behavior:**
- Fetch data for both tokens
- Show side-by-side comparison table
- Highlight the winner on key metrics (Fees, Volume, Growth, Holders)
- Give short insight which one is currently stronger

---

## 5. Smart Claim Suggestion

**User:**
Check fees for this token 0x...

**Expected Behavior:**
- Show full dashboard
- If claimableWeth ≥ 0.01 → strongly recommend claiming
- If claimableWeth between 0.003 – 0.01 → soft suggestion
- If very low → just show data

---

## 6. Historical Deep Dive

**User:**
Show detailed earnings history for CLAWD  
atau  
Best day of this token

**Expected Behavior:**
- Show lifetimeBestDay
- Show last 14–30 days daily earnings
- Calculate trend (7d vs previous 7d)
- Give short performance summary

---

## 7. Quick Commands (High Priority Triggers)

These should always activate TTTracker strongly:

- “TTTracker”
- “Show dashboard”
- “Fee report”
- “Agent analytics”
- “How much fees”
- “Token performance”
- “Ranking agents”
- “My earnings”

---

## Response Quality Rules

- Always use clean markdown tables
- Always convert WETH to approximate USD
- Never invent numbers
- Be concise but complete
- End with 1–3 useful next actions
- Maintain professional + slightly sharp tone
