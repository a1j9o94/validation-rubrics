# Regulatory Application — Judgment Rubric

> **HOLDOUT**: This file must NEVER be shown to the builder agent. It is injected into the validator's context only.

> **GATE RULE**: Before scoring this rubric, you MUST have run checks.md. If ANY check in checks.md failed, the overall result is **FAIL** regardless of rubric scores. You may still score dimensions for diagnostic purposes, but clearly mark the overall assessment as FAIL due to checks failure.

Score each dimension 1-5. A passing work plan scores ≥ 3 on every dimension and ≥ 3.5 average.

## 1. Research Depth (1-5)

**5 — Excellent:** Requirements sourced from primary legal text (statutes, administrative code), cross-referenced with agency guidance documents, and supplemented with practical knowledge (common rejection reasons, processing bottlenecks). Distinguishes between what's legally required and what's practically advisable.

**3 — Adequate:** Requirements sourced from official agency website. Accurate but surface-level — lists what the agency says you need without deeper analysis of edge cases, common pitfalls, or practical tips.

**1 — Failing:** Requirements sourced from blog posts, outdated articles, or AI training data without verification. May include requirements from the wrong jurisdiction, wrong license type, or outdated regulations.

**Common failure modes:**
- Citing requirements from a different state's program
- Using requirements from a previous year's application cycle without verifying current year changes
- Missing recently enacted amendments or rule changes
- Confusing different license categories (e.g., dispensary vs. infuser vs. cultivator)

## 2. Completeness of Requirements (1-5)

**5 — Excellent:** Every document, form, fee, background check, facility requirement, personnel requirement, and operational plan component is individually enumerated. Nothing is summarized as "various" or "etc." Includes both obvious requirements and non-obvious ones (e.g., surety bonds, local zoning approval, facility security plans).

**3 — Adequate:** Major requirements are all listed. May miss some ancillary requirements (local permits, insurance specifics, post-approval ongoing compliance).

**1 — Failing:** Missing major categories of requirements. Lists 5-6 items when there are 15+. Treats "submit application with required documents" as a single checklist item.

**Common failure modes:**
- Missing local/municipal requirements (only covering state level)
- Missing post-approval requirements that must be planned for during application
- Missing personnel-specific requirements (background checks, training certifications)
- Omitting facility/premises requirements when no facility is secured yet

## 3. Timeline Realism (1-5)

**5 — Excellent:** Timeline accounts for real-world delays — background check processing times, document procurement lead times, legal review cycles, facility search timelines. Includes buffer. Flags hard deadlines vs. soft targets. If the timeline is already infeasible, says so clearly.

**3 — Adequate:** Timeline is present and roughly reasonable. May be optimistic about certain steps. Identifies the application deadline but doesn't deeply model the lead times for each requirement.

**1 — Failing:** No timeline, or a timeline that's obviously unrealistic (e.g., "complete application in 3 days" when background checks alone take 2-4 weeks). Doesn't flag that a deadline has passed or is imminent.

**Common failure modes:**
- Assuming background checks are instant
- Not accounting for lawyer/accountant availability
- Ignoring the time to secure a facility or letter of intent for premises
- Not flagging that the application window may already be closed

## 4. Cost Accuracy (1-5)

**5 — Excellent:** All costs enumerated with specific dollar amounts, sourced from official fee schedules. Includes both direct costs (application fees, license fees) and indirect costs (legal fees, consultant fees, facility deposits, insurance). Provides a total estimated cost range.

**3 — Adequate:** Application and license fees are accurate. Some indirect costs mentioned but not fully estimated. Total cost range is approximate.

**1 — Failing:** Fees are wrong, missing, or stated without sources. Major cost categories omitted. No total estimate.

**Common failure modes:**
- Citing fees from a different license category
- Missing social equity fee reductions when applicable
- Omitting ongoing compliance costs (annual renewals, testing fees, reporting)
- Ignoring legal fees which are often the largest single cost

## 5. Actionability (1-5)

**5 — Excellent:** A non-expert could pick up this document and begin executing immediately. First step is crystal clear. Each subsequent step has enough detail to act on (who to contact, what to prepare, what form to fill out). Decision points are flagged ("if you qualify for social equity, do X; if not, do Y"). Red flags and deal-breakers are called out early.

**3 — Adequate:** Steps are listed in reasonable order. An experienced person could follow it. May require some additional research to execute certain steps.

**1 — Failing:** Requirements are listed as facts, not as actions. No sequencing. No prioritization. Reading it doesn't make you feel closer to actually doing it.

**Common failure modes:**
- Listing requirements without saying how to satisfy them
- No prioritization — item #1 is as important as item #15
- Missing "go/no-go" decision points where the applicant should stop and evaluate
- No distinction between what the applicant does vs. what a professional (lawyer/accountant) does

## Scoring

| Score | Meaning |
|-------|---------|
| 5 | Exceptional — could serve as a professional consultant's deliverable |
| 4 | Strong — minor gaps, but fundamentally reliable and actionable |
| 3 | Adequate — usable but needs supplemental research for execution |
| 2 | Weak — significant gaps that could lead to a failed or rejected application |
| 1 | Failing — unreliable enough to be harmful if followed |

**Pass threshold:** ≥ 3 on every dimension AND ≥ 3.5 average.

**Feedback generation:**
- For scores of 1-2: Generate Tier 3 feedback (show specific missing requirement or incorrect fact)
- For scores of 3: Generate Tier 2 feedback (describe category of what's missing)
- For scores of 4-5: No feedback needed
