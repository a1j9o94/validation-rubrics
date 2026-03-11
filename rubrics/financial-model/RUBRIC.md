# Financial Model — Judgment Rubric

> **HOLDOUT**: This file must NEVER be shown to the builder agent. It is injected into the validator's context only.

Score each dimension 1-5. A passing model scores ≥ 3 on every dimension and ≥ 3.5 average.

## 1. Assumption Quality (1-5)

**5 — Excellent:** Assumptions are sourced (industry benchmarks, comparable companies, or stated rationale), internally consistent, and include sensitivity ranges. Key assumptions are clearly identified and prioritized.

**3 — Adequate:** Assumptions are stated and reasonable but not sourced. No obvious contradictions. Missing sensitivity analysis.

**1 — Failing:** Assumptions are unstated, contradictory, or implausible. Growth rates appear arbitrary. Key assumptions (market size, conversion rates, pricing) are missing or unrealistic.

**Common failure modes:**
- "Hockey stick" revenue with no mechanism explaining the inflection
- Assuming 100% of addressable market captured
- Cost assumptions that don't scale with revenue (e.g., fixed COGS at 10x revenue)
- Confusing TAM with realistic serviceable market

## 2. Scenario Robustness (1-5)

**5 — Excellent:** Multiple scenarios (base, optimistic, pessimistic) with clearly different assumption sets. Scenarios reveal what drives profitability — you can see the sensitivity. Break-even analysis included.

**3 — Adequate:** Base case is well-built. At least one alternate scenario exists but may not vary the right assumptions. Break-even identifiable but not explicitly called out.

**1 — Failing:** Single scenario only. No sensitivity analysis. No way to understand what happens if key assumptions are wrong.

**Common failure modes:**
- "Pessimistic" scenario is just base case minus 10% — not a real stress test
- Scenarios vary revenue but not costs (or vice versa)
- No identification of which assumptions the model is most sensitive to

## 3. Operational Realism (1-5)

**5 — Excellent:** Model reflects how the business actually operates. Hiring ramps match growth. Inventory/COGS timing reflects production cycles. Marketing spend has a lagged effect on revenue. Seasonal patterns included where relevant.

**3 — Adequate:** Major operational dynamics captured. Some simplifications but nothing that breaks the narrative. Timing is roughly right.

**1 — Failing:** Model is purely financial with no operational logic. Revenue appears from nowhere. Costs are flat percentages with no connection to real activities. No consideration of timing, ramps, or capacity constraints.

**Common failure modes:**
- Revenue starts at full run rate in month 1 (no ramp)
- Hiring is instantaneous (no recruiting timeline)
- Manufacturing costs don't include setup, tooling, or minimum order quantities
- Marketing-to-revenue connection is assumed, not modeled

## 4. Cash Flow Awareness (1-5)

**5 — Excellent:** Cash flow is the primary planning tool, not an afterthought. Working capital dynamics modeled (accounts receivable, payable, inventory). Funding requirements clearly identified with timing. Burn rate and runway calculated.

**3 — Adequate:** Cash flow statement exists and reconciles. Basic funding needs identified. Working capital not deeply modeled but not ignored.

**1 — Failing:** Cash flow is missing or doesn't reconcile. No burn rate. No runway calculation. Funding needs unclear. Model could show profitability while the company runs out of cash.

**Common failure modes:**
- Profitable on P&L but negative cash flow (not flagged)
- No consideration of payment terms (assumes instant payment)
- Inventory buildup not reflected in cash flow
- Capital expenditures missing from cash flow

## 5. Decision Utility (1-5)

**5 — Excellent:** The model is a *decision tool*, not just a projection. You can change inputs and see the impact. Key decisions are modeled (when to hire, when to raise, when to launch new products). The model tells you what to do, not just what might happen.

**3 — Adequate:** Model projects outcomes but doesn't clearly guide decisions. You could use it for planning with some additional work. Input-output relationships are traceable.

**1 — Failing:** Model is static — a set of numbers, not a tool. Changing assumptions requires rebuilding. No clear connection between decisions and outcomes. Useful only as a slide in a pitch deck.

**Common failure modes:**
- Hardcoded structure that breaks when you change one assumption
- No "what-if" capability
- Model answers "what do we project?" but not "what should we do?"
- Metrics that matter for decisions (CAC, LTV, payback period, runway) not calculated

## Scoring

| Score | Meaning |
|-------|---------|
| 5 | Exceptional — could present to a sophisticated investor or board |
| 4 | Strong — minor gaps but fundamentally sound |
| 3 | Adequate — usable for internal planning, needs work for external |
| 2 | Weak — significant gaps that undermine reliability |
| 1 | Failing — fundamental problems that require a rebuild |

**Pass threshold:** ≥ 3 on every dimension AND ≥ 3.5 average.

**Feedback generation:**
- For scores of 1-2: Generate Tier 3 feedback (counter-example showing the problem)
- For scores of 3: Generate Tier 2 feedback (behavioral description of what's missing)
- For scores of 4-5: No feedback needed
