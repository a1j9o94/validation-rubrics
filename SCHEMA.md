# Schema Reference

## Directory Structure

Each rubric lives in its own directory under `rubrics/`:

```
rubrics/<rubric-name>/
├── RUBRIC.md              # Overview: what, when, prerequisites (REQUIRED)
├── checks.md              # Automated checks — hard gate (REQUIRED)
├── rubric.md              # Judgment criteria — holdout (REQUIRED)
├── config.yaml            # Metadata and scoring config (REQUIRED)
└── examples/              # Pass/fail examples (RECOMMENDED)
    ├── pass.md
    └── fail.md
```

## config.yaml Schema

```yaml
# REQUIRED fields
name: string               # kebab-case identifier, must match directory name
version: string            # semver (e.g., "1.0.0")
risk_tier: integer         # 0-4, determines validation pipeline (see below)
domain: list[string]       # applicable domains (e.g., ["finance", "startup"])

# REQUIRED — scoring
pass_threshold:
  min_per_dimension: number  # minimum score on every rubric dimension to pass
  min_average: number        # minimum average across all dimensions to pass

dimensions: list[string]   # list of rubric dimension names, must match rubric.md

# OPTIONAL — validator configuration
checks_executable: boolean   # default: false. If true, checks.md can be run as a script
rubric_model_preference: string  # "same", "different", or "any" (default: "any")
                                 # "different" = use a different base model than the builder
min_validator_capability: string # "basic", "medium", or "high" (default: "medium")
                                 # guides model selection for the validator agent

# OPTIONAL — feedback configuration  
default_feedback_tier: integer   # 1, 2, or 3 (default: varies by risk_tier)
                                 # tier 1 = category only
                                 # tier 2 = behavioral description
                                 # tier 3 = counter-example without assertion
```

## Risk Tiers

| Tier | Level | Validation Pipeline | Default Feedback Tier |
|------|-------|--------------------|-----------------------|
| 0 | Reversible, internal | Post-hoc sampling only | 1 |
| 1 | Internal, low-stakes | Single-agent rubric check | 2 |
| 2 | External, recoverable | Multi-agent review | 2 |
| 3 | External, consequential | Multi-agent + human gate | 3 |
| 4 | Irreversible | Human-only with agent advisory | 3 |

## Validation Logic

```
1. Run checks.md against work product
2. IF any check fails → OVERALL RESULT = FAIL
   - Rubric scoring MAY still run for diagnostic purposes
   - Rubric scores CANNOT override a checks failure
   - Generate feedback for failed checks
3. IF all checks pass → Run rubric.md scoring
4. Score each dimension 1-5
5. IF any dimension < pass_threshold.min_per_dimension → FAIL
6. IF average score < pass_threshold.min_average → FAIL
7. OTHERWISE → PASS
8. Generate feedback per feedback tier for any dimension scoring below 4
```

This is the canonical validation flow. Validator agents must follow this sequence. The checks gate is not advisory — it is a hard requirement.

## checks.md Format

Checks should be written as markdown checklists with clear, binary conditions:

```markdown
## Section Name
- [ ] **Check name.** Description of what to verify. Clear pass/fail condition.
- [ ] **Another check.** Another binary condition.
```

Each check must be:
- **Binary** — pass or fail, no partial credit
- **Deterministic** — same input should always produce the same result
- **Specific** — "balance sheet balances" not "financials look right"
- **Independent** — each check evaluable on its own

## rubric.md Format

Rubric dimensions should follow this template:

```markdown
## N. Dimension Name (1-5)

**5 — Excellent:** Description of what excellence looks like.

**3 — Adequate:** Description of the minimum acceptable standard.

**1 — Failing:** Description of what failure looks like.

**Common failure modes:**
- Specific pattern that causes scores of 1-2
- Another common failure
```

Every rubric.md must include:
- The holdout warning: `> **HOLDOUT**: This file must NEVER be shown to the builder agent.`
- Score anchors at 5, 3, and 1 for every dimension
- Common failure modes for every dimension
- Pass threshold definition
- Feedback generation rules per score level
```

