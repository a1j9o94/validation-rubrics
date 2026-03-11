# Validation Rubrics

Open-source validation criteria for AI agent work — the test suites for knowledge work.

## What This Is

When AI agents build software, you can validate with test suites. But agents also write financial models, sales emails, legal docs, marketing copy, and strategy memos. Those don't have test suites.

This repo provides **validation rubrics**: structured criteria that a validator agent uses to evaluate another agent's work, without the producing agent ever seeing the criteria. Think of it like clinical trial blinding — the builder can't game what it can't see.

Each rubric has two layers:
- **Checks** — deterministic, automated, binary pass/fail (e.g., "balance sheet balances")
- **Rubric** — judgment-based evaluation criteria (e.g., "are the growth assumptions defensible?")

## Structure

```
rubrics/
  financial-model/
    RUBRIC.md           # Overview: when to use, what it validates
    checks.md           # Automated/deterministic checks
    rubric.md           # Judgment criteria (holdout — never shown to builder)
    examples/
      pass.md           # Example of passing work with annotations
      fail.md           # Example of failing work with annotations
    config.yaml         # Metadata: risk tier, domain, version
  sales-outreach/
    ...
  investor-pitch/
    ...
```

## How It Works

1. A **builder agent** gets the task (e.g., "build a 3-year financial model for a THC edibles company")
2. A **validator agent** gets this repo's rubric injected into its context
3. The builder **never sees** the rubric — structural separation, not just policy
4. Validator runs `checks.md` first (fast, deterministic)
5. If checks pass, validator applies `rubric.md` (judgment-based, scored)
6. If validation fails, feedback follows a tiered model:
   - **Tier 1:** Category only ("balance sheet section failed")
   - **Tier 2:** Behavioral description ("model produces incorrect totals for months with seasonal adjustments")
   - **Tier 3:** Counter-example without assertion (show the failing input but not the expected output)

## Risk Tiers

Rubrics are tagged with a risk tier that determines the validation pipeline:

| Tier | Risk Level | Validation Required |
|------|-----------|-------------------|
| 0 | Reversible, internal | Post-hoc sampling only |
| 1 | Internal, low-stakes | Single-agent rubric check |
| 2 | External, recoverable | Multi-agent review |
| 3 | External, consequential | Multi-agent + human gate |
| 4 | Irreversible | Human-only with agent advisory |

## Contributing

We welcome rubrics for any domain. A good rubric:
- Has clear, specific checks that can be automated
- Has judgment criteria that are evaluable by a capable LLM
- Includes pass/fail examples with annotations explaining *why*
- Specifies the risk tier honestly
- Doesn't assume a specific tech stack or toolchain

See [CONTRIBUTING.md](CONTRIBUTING.md) for the full guide.

## Background

This project emerges from work on [Dark Factory](https://github.com/a1j9o94/df-cli) (agent build orchestration with holdout validation) and research into applying corporate governance patterns (maker-checker, SOX separation of duties, clinical trial blinding) to AI agent organizations.

The core insight: **the patterns for validating knowledge work already exist in corporate governance — they just haven't been codified for machines.**

## License

MIT
