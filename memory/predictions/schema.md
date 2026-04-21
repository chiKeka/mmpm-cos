# Prediction Record Schema

Every Council output produces a prediction record in `predictions/{YYYY-MM-DD_programme-slug_decision-slug}/prediction.md`. The record uses the structure below. YAML frontmatter is machine-extractable; prose sections are for human audit.

## Directory naming

```
{YYYY-MM-DD}_{programme-slug}_{decision-slug}/
```

Example: `2026-04-20_edmonton-vlse_dp2-alignment-tech/`

## `prediction.md` structure

```markdown
---
prediction_id: {YYYY-MM-DD}_{programme-slug}_{decision-slug}
decision_moment: {ISO-8601 date or date-range, as known at decision time}
programme: {canonical programme name}
decision: {one-line decision summary}
council_run_date: {YYYY-MM-DD}
council_run_id: {path to council output if stored}
model_version: {e.g., claude-opus-4-7}
primary_recommendation: {one-line}
primary_recommendation_direction: {proceed | proceed-with-conditions | defer | reject | reframe}
primary_confidence: {very_low | low | moderate | moderate-to-high | high | very_high}
sub_options_preserved: {list of alternative options Council flagged}
key_risks_predicted: {list of {risk_name, severity, mitigation_proposed}}
red_team_failure_scenarios: {list of {scenario_name, likelihood, severity}}
unresolved_tensions: {list of {tension_name, agents_dissenting, chair_preference}}
escalation_flagged: {list of questions escalated for human judgment}
base_rate_framings: {list of {reference_class, predicted_outturn_range, applied_to_case_as}}
structural_critiques_applied: {list of named critiques per Evidence Quality Gate routines}
agents_consulted: {list of agent names}
operator_notes: {string — any notes the operator thinks are relevant for future calibration}
---

# Prediction Record — {programme} — {decision}

## 1. Decision context as known at decision moment

{One paragraph summary — enough that a future reviewer can understand what Council was asked, without reading the full Council output.}

## 2. What Council recommended and predicted

{Summary of the primary recommendation, alternative options, key risks, Red Team scenarios, unresolved tensions, escalation flags. This prose is extracted from the Council synthesis but organised for auditability.}

## 3. What Council's confidence calibration implied

- Primary recommendation confidence: {e.g., MODERATE-TO-HIGH} → implies Council would be surprised (moderately) if this recommendation proved wrong.
- Key-risk severity ratings: {enumerate HIGH/CRITICAL items} → Council expects these to materialise unless mitigated.
- Red Team likelihood assessments: {enumerate} → Council treats these as non-tail scenarios.
- Base-rate applications: {enumerate predicted outturn ranges} → Council expects realised outcomes within these ranges unless this case is the exception the reference class implies.

## 4. Dissent preserved

{Summary of Contrarian's softening, any agent disagreements, and specifically which dissenting views Chair acknowledged but did not adopt. The calibration report later checks whether these dissenting views proved prescient.}

## 5. Auditable predictions

List of specific, testable predictions extracted from the synthesis. Each should be worded so a future reviewer can unambiguously mark it as Confirmed / Contradicted / Partially-Confirmed / Not-Yet-Known.

- P1: {specific prediction, e.g., "Capital cost outturn will exceed Business Plan estimate by at least 30% in real terms over the programme lifetime."}
- P2: {...}
- P3: {...}

Aim for 5-10 testable predictions per major Council output; fewer for smaller runs.
```

## `outcome.md` structure (populated later, human-entered)

```markdown
---
outcome_id: {matches prediction_id}
outcome_date: {YYYY-MM-DD when this record was populated}
outcome_horizon: {partial | complete} — is the programme still unfolding or concluded?
outcome_source: {citation of outcome evidence — NAO report, news coverage, Auditor-General review, etc.}
populator: {who filled this in}
---

# Outcome Record — {programme} — {decision}

## What happened

{Factual summary of outcomes. Distinguish clearly between programme-complete outcomes and partial-horizon signals.}

## Per-prediction audit

For each P# in the prediction record, mark and explain:

- **P1** — Confirmed / Contradicted / Partial / Not-Yet-Known. {Evidence.}
- **P2** — ...
- ...

## Did Council's preserved dissent prove prescient?

For each dissent item in prediction §4, assess whether the dissenting view better tracked the actual outcome than the primary recommendation. "Contrarian flagged PPP Canada funding-window risk; this did materialise and forced re-baselining in 2014" is a structural calibration datum.

## Were there outcome dimensions Council did not predict?

If the programme produced significant outcomes that Council's deliberation did not anticipate (positively or negatively), list them. Unpredicted outcomes are the most important calibration signal — they indicate dimensions the current routing rules and agent definitions are blind to.

## Source confidence

How reliable is the outcome evidence? A NAO post-mortem is strong; a single news article is weak; an in-flight programme with partial signals is intermediate.
```

## `audit.md` structure (populated at calibration review)

```markdown
---
audit_id: {matches prediction_id}
audit_date: {YYYY-MM-DD of the calibration report this audit feeds}
auditor: {who ran the calibration review}
calibration_report_ref: {path to the calibration report this feeds into}
---

# Calibration Audit — {programme} — {decision}

## Confidence calibration

Compare Council's confidence levels to outcome quality. Was Council too confident? Under-confident? Appropriately calibrated?

## Dissent validation

Did preserved dissent track outcomes better than primary recommendations?

## Structural findings

What patterns did this case reveal about specific agent behaviour? (Feeds into the calibration report's adjustment proposals.)

## Proposed adjustments

Specific changes to agent definitions, routing rules, or output contracts based on this case. These feed the aggregate calibration report which the designer then acts on (or does not).
```

## Provenance

This schema was drafted 2026-04-21 as part of the MMPM-COS feedback-loop infrastructure. Future schema changes should be versioned and should not retroactively invalidate existing prediction records.
