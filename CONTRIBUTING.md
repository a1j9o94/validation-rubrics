# Contributing to Validation Rubrics

## Adding a New Rubric

1. Create a directory under `rubrics/` with a descriptive name (kebab-case)
2. Include all required files:

### Required Files

**`RUBRIC.md`** — Overview
- What this rubric validates
- When to use it (and when NOT to)
- Prerequisites (what the builder should have been asked to produce)
- Related rubrics

**`checks.md`** — Automated Checks
- Deterministic, binary pass/fail criteria
- Should be evaluable programmatically where possible
- Format: checklist with clear conditions
- These run FIRST — if checks fail, rubric evaluation is skipped

**`rubric.md`** — Judgment Criteria (HOLDOUT)
- This file is NEVER shown to the builder agent
- Evaluation criteria that require judgment, not just verification
- Scored on a clear scale (e.g., 1-5 per dimension, with anchors)
- Include: what "passing" looks like, what "failing" looks like, common failure modes

**`config.yaml`** — Metadata
```yaml
name: your-rubric-name
version: 1.0.0
risk_tier: 2          # 0-4, see README for definitions
domain:               # list of applicable domains
  - finance
  - startup
checks_executable: false   # true if checks.md can run as a script
rubric_model_preference: different  # 'same', 'different', or 'any'
min_validator_capability: high      # 'basic', 'medium', 'high'
```

**`examples/pass.md`** — Passing Example
- A concrete example of work that passes both checks and rubric
- Annotated: explain WHY each criterion is met

**`examples/fail.md`** — Failing Example
- A concrete example of work that fails
- Annotated: explain which criteria failed and why
- Include examples of subtle failures, not just obvious ones

## Quality Standards

- **Be specific.** "Is it good?" is not a rubric criterion. "Does the financial model include sensitivity analysis for the top 3 revenue assumptions?" is.
- **Be testable.** Every criterion should be evaluable by a capable LLM with domain knowledge.
- **Include edge cases.** The best rubrics catch subtle failures that a naive reviewer would miss.
- **Version your rubrics.** When you improve criteria, bump the version in config.yaml.
- **Don't assume tools.** Rubrics should be framework-agnostic — evaluable by any capable model.

## Feedback Tier Guidelines

When writing rubric criteria, consider how feedback should be generated for each:

- **Tier 1 feedback** (category): "Revenue projections section did not pass"
- **Tier 2 feedback** (behavioral): "The model assumes linear growth but the market has seasonal patterns"
- **Tier 3 feedback** (counter-example): "When Q4 inputs are doubled, the annual total doesn't change"

Higher-risk rubrics should default to Tier 3 feedback (maximum information for the builder to fix the issue without revealing the acceptance criteria).
