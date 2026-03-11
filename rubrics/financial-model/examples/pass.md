# Financial Model — Passing Example

## Context
3-year monthly financial model for a THC edibles startup. Two founders, AI-first operations, ~$10K/month AI spend, manufacturing outsourced initially.

## Why This Passes

### Checks ✅
- Balance sheet balances in all 36 months
- Cash flow reconciles to balance sheet cash
- Net income flows to retained earnings
- All growth rates trace to assumptions tab
- No hardcoded calculations — all formulas reference named inputs
- Three statements present + assumptions page

### Rubric Scores

**Assumption Quality: 4/5**
- Revenue builds from: # dispensaries × sell-through rate × units per store × price per unit
- Each component has a stated source ("IL dispensary average sell-through for new brands: 15-25 units/month, source: Headset data")
- Growth in dispensary count modeled as a ramp (5 in month 1, adding 2-3/month)
- Missing: formal sensitivity ranges on the assumptions page (stated as single values)

**Scenario Robustness: 4/5**
- Three scenarios: Conservative (50% of base revenue, higher COGS), Base, Aggressive (2x dispensary growth)
- Break-even month identified in each scenario (month 14, 18, 24 respectively)
- Shows that COGS percentage is the swing variable, not volume
- Missing: tornado chart showing assumption sensitivity ranking

**Operational Realism: 5/5**
- Manufacturing has 90-day lead time before first delivery
- Infuser license application timeline modeled (6-month gap between application and approval)
- Seasonal pattern: 20% bump in holiday months
- AI operations costs ($10K/month) start from month 1, not when revenue starts
- Hiring: no additional employees modeled — founders only, consistent with AI-first thesis

**Cash Flow Awareness: 4/5**
- Burn rate and runway calculated monthly
- Funding requirements identified: $150K needed by month 3, second raise of $200K at month 12 if base case
- Payment terms modeled: dispensaries pay net-30
- Missing: inventory financing dynamics (assumes COD from manufacturer)

**Decision Utility: 4/5**
- Model answers: "When do we need to raise?" "How many dispensaries to break even?" "What happens if COGS is 10% higher?"
- Input cells clearly marked — changing dispensary count or pricing ripples through everything
- Key metrics dashboard: CAC per dispensary, revenue per dispensary, burn rate, runway months
- Missing: explicit decision triggers ("if dispensary #20 says no, pivot to X")

**Average: 4.2/5** ✅ Passes (≥ 3.5 average, no dimension below 3)
