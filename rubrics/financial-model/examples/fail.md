# Financial Model — Failing Example

## Context
Same THC edibles startup. Different model produced by a builder agent.

## Why This Fails

### Checks ❌ (3 failures)

1. **Balance sheet doesn't balance in months 11-12.** Assets exceed L+E by $23K. Cause: a manual adjustment to inventory was added to assets but not reflected in liabilities or equity.
2. **Hardcoded revenue in months 7-12.** Months 1-6 use formulas (dispensaries × units × price). Months 7-12 switch to typed values ($45,000, $52,000, etc.) with no formula — likely copy-pasted from a different version.
3. **Missing cash flow statement.** Only P&L and balance sheet present. Cash position mentioned in a note but not formally modeled.

*Validation stops here — checks failed, rubric not applied.*

---

## If Rubric Were Applied (for illustration)

**Assumption Quality: 2/5**
- Revenue assumes 50 dispensaries by month 6 with no ramp — jumps from 0 to 50 in month 1
- No source for pricing ($25/unit) or sell-through estimates
- COGS is a flat 40% of revenue with no connection to actual manufacturing costs, MOQs, or packaging
- Growth rate of 30% MoM stated but not explained — 30% of what?

**Scenario Robustness: 1/5**
- Single scenario only
- No break-even analysis
- No sensitivity on any assumption
- If pricing is wrong by 20%, the model gives no signal

**Operational Realism: 1/5**
- Revenue starts in month 1 — no license application timeline, no manufacturing lead time
- Hiring of a "marketing manager" at $80K in month 2 contradicts the 2-person AI-first thesis
- No seasonal patterns
- AI costs not modeled at all

**Cash Flow Awareness: 1/5**
- No cash flow statement
- No burn rate or runway calculation
- The P&L shows profitability by month 8 but there's no way to know if the company has cash to survive to month 8
- No funding requirements identified

**Decision Utility: 2/5**
- Model projects numbers but doesn't help make decisions
- You can't change dispensary count without manually retyping 12 months of revenue
- No key metrics (CAC, LTV, runway, break-even)
- The model answers "what might revenue be?" but not "what should we do?"

**Average: 1.4/5** ❌ Fails (below 3 on 4 of 5 dimensions)

## Feedback That Would Be Generated

**Tier 3 (counter-example, no assertion):**

> "When the dispensary count input is changed from 50 to 25, revenue in months 7-12 doesn't change. The model appears to have disconnected inputs from outputs in the second half of the projection."

> "The balance sheet shows total assets of $187,000 in month 11 but liabilities plus equity sum to $164,000. Investigate the inventory line."

Note: feedback identifies the *symptom* (revenue doesn't change, balance sheet doesn't balance) without telling the builder *what the correct values should be*. The builder must reason about the fix from context.
