# Calibration Report — {YYYY-MM-DD}

Template for the periodic calibration report produced by `/calibrate`. The report compares predictions against outcomes across all prediction records with populated outcome.md files.

## Metadata

```yaml
report_date: {YYYY-MM-DD}
reporting_window: {YYYY-MM-DD to YYYY-MM-DD}
predictions_reviewed: {N}
predictions_with_outcomes: {M}
model_version_range: {e.g., claude-opus-4-7 through 4.8}
```

## 1. Aggregate calibration

### Confidence calibration

Across the M outcomed predictions, compute:

| Confidence level | Cases | Confirmed | Contradicted | Partial | Brier-style score |
|------------------|-------|-----------|--------------|---------|-------------------|
| very_high | | | | | |
| high | | | | | |
| moderate-to-high | | | | | |
| moderate | | | | | |
| low | | | | | |
| very_low | | | | | |

**Reading**: Council's stated confidence should predict outcome confirmation. If "high-confidence" predictions are confirmed 55% of the time, Council is systematically overconfident at the top end. If "moderate" predictions are confirmed 85%, Council is under-confident mid-range.

### Dissent calibration

How often did Council's preserved dissent (Contrarian or agent disagreement) track outcomes better than the primary recommendation?

| Decision class | N cases | Dissent prescient | Primary prescient | Tie / both wrong |
|----------------|---------|-------------------|-------------------|-------------------|
| P3 delivery model | | | | |
| Infrastructure route commitment | | | | |
| Late-programme opening-date | | | | |
| ... | | | | |

If dissent is systematically prescient in a decision class, Chair synthesis is over-weighting consensus against Contrarian in that class.

## 2. Per-agent calibration

For each agent, aggregate across cases:

- How often did this agent's findings prove directionally correct?
- Which specific predictions by this agent were most / least accurate?
- Are there decision classes where this agent underperforms the others?

Format:

```
### Risk Agent
- N assessments: {N}
- Directional correctness: {%}
- Notable accurate predictions: {list}
- Notable missed predictions: {list}
- Systematic pattern: {e.g., "underweights demand-shortfall probability on rail cases"}
- Proposed adjustment: {specific edit to agent definition}
```

Run for each of the 17 agents (post-QA addition) plus Chair.

## 3. Per-routing-rule calibration

Which mandatory routing rules produced the highest-value findings? Which were over-triggered (invoked unnecessarily) or under-triggered (should have fired but did not)?

## 4. Structural patterns

Across all cases, identify cross-case patterns that are not agent-specific:

- Blind spots the entire system missed (outcomes not predicted by any agent).
- Framing choices Council consistently applied that shaped outcomes positively or negatively.
- Cases where practitioner-context retrieval (per `memory/practitioner-context/`) changed the answer — or did not, when it should have.

## 5. Proposed adjustments

Specific, actionable adjustments. Each has:
- What to change (file path and specific text)
- Why (evidence basis: which cases support this)
- Severity (minor clarification / substantive revision / architectural change)

Format:
```
### Adjustment 1: {short name}
- File: agents/risk-uncertainty-fragility-agent.md § Canonical Diagnostic Heuristics H2
- Change: Add Canadian P3 pre-2018 explicit "thin reference class, apply 1.5× uplift to global base rate"
- Evidence: Cases A, B, C showed Council under-predicted cost outturn by ~50% on Canadian P3 transit; global Flyvbjerg rate ~45% produced ~68% outturn under pattern
- Severity: substantive revision
```

## 6. Meta-calibration

How confident is the calibrator in this report itself? Are there patterns flagged here that deserve independent review before being applied? Which proposed adjustments are robust and which are suggestive?

## 7. Adjustments accepted / deferred

To be populated after the designer reviews. Adjustments committed to agent definitions are marked here with their commit SHA. Adjustments deferred are flagged with a reason.

## 8. Next review window

When the next calibration report should be produced. Default: every 6 months, or when 10+ new outcomed predictions accumulate, whichever is sooner.
