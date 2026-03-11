# Financial Model — Automated Checks

These are deterministic checks. Each is binary pass/fail. Run these BEFORE applying the judgment rubric.

## Structural Integrity

- [ ] **Balance sheet balances.** For every period: Assets = Liabilities + Equity. Tolerance: ±$1 (rounding only).
- [ ] **Cash flow reconciles.** Ending cash on cash flow statement matches cash on balance sheet for every period.
- [ ] **P&L flows to balance sheet.** Net income on P&L matches the change in retained earnings on balance sheet (adjusted for dividends/distributions).
- [ ] **Opening balances carry forward.** Each period's opening balance equals the prior period's closing balance. No gaps or manual overrides.

## Formula Integrity

- [ ] **No hardcoded numbers in calculation cells.** Revenue, COGS, expenses, and projections must derive from input assumptions, not typed values. Exception: historical actuals can be hardcoded if clearly labeled.
- [ ] **Growth rates derive from assumptions.** If revenue grows 15% YoY, there must be a traceable input assumption that says 15%, not a formula that says `= prior * 1.15` with no reference.
- [ ] **Unit economics are consistent.** Price × volume = revenue. COGS per unit × volume = total COGS. No disconnected calculations.
- [ ] **No circular references.** Unless explicitly documented and intentionally managed with iteration settings.

## Completeness

- [ ] **All three statements present.** P&L (income statement), balance sheet, and cash flow statement. A model missing any one is incomplete.
- [ ] **Assumptions page/section exists.** All key inputs collected in one place, not scattered across the model.
- [ ] **Time granularity matches spec.** If weekly was requested, it's weekly. If monthly was requested, it's monthly. Not a mix.
- [ ] **Full time horizon covered.** If 3 years was requested, all 36 months (or 156 weeks) are present.

## Sanity Checks

- [ ] **No negative revenue.** Revenue is ≥ 0 in all periods (unless explicitly modeling refunds/returns).
- [ ] **Cash doesn't go deeply negative without funding.** If cash balance goes negative, there should be a corresponding debt/equity raise or a clear note that this represents a funding gap.
- [ ] **Margins are within plausible range.** Gross margins aren't >99% or < -50% without explanation. Operating margins aren't consistently >50% for a non-software business without explanation.
- [ ] **Headcount math works.** If model includes payroll: salary × headcount × months = total payroll expense (±benefits loading).
- [ ] **Tax rate applied.** If model is post-tax, a tax rate is applied. If pre-tax, it's clearly labeled.

## Formatting

- [ ] **Periods are labeled.** Every column has a date or period identifier.
- [ ] **Units are specified.** Dollars, thousands, millions — stated clearly.
- [ ] **Inputs vs. outputs are visually or structurally distinguished.** Assumptions/inputs are separate from calculated outputs.
