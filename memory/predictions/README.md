# Prediction Log

**Purpose**: Convert MMPM-COS from a write-only memory system into a feedback-loop system. Every Council output writes its predictions, confidence levels, and framing choices here. Over time, outcomes are logged against predictions. Periodic calibration review (via `/calibrate`) compares the two and surfaces empirical drift, producing adjustments to agent priors.

## Why this exists

Added 2026-04-21 as the first structural improvement from the post-evaluation retrospective. The original MMPM-COS design had `memory/decisions/` for write-only decision logs and `memory/practitioner-context/` for user annotations, but no mechanism for the system to learn from its own predictions against realised outcomes. That meant MMPM-COS in year 10 would be as calibrated as year 1 — a static doctrine layer rather than a maturing analytical system.

This directory closes that gap. It is the system's empirical self-calibration infrastructure.

## Directory structure

```
memory/predictions/
├── README.md                          # This file
├── schema.md                          # Structure of a prediction record
├── calibration-report-template.md     # Format for periodic calibration reports
├── predictions/                       # One subdirectory per Council run
│   └── {YYYY-MM-DD_programme-slug_decision-slug}/
│       ├── prediction.md              # The extracted predictions at decision moment
│       ├── outcome.md                 # Populated later when outcome is known
│       └── audit.md                   # Populated at calibration review
└── reports/                           # Periodic calibration reports
    └── {YYYY-MM-DD}_calibration-report.md
```

## Workflow

### At Council invocation (automatic)

The Chair, as the final step of the 12-step orchestration flow (Memory Write), extracts predictions from the synthesis and writes `predictions/{timestamp_slug}/prediction.md` per the schema in `schema.md`. This is not optional; it is part of synthesis.

### When outcome becomes known (human-entered)

The user (designer-scorer or practitioner) edits the relevant `outcome.md` file to record what actually happened. This can be immediate (for short-horizon decisions) or years later (for long-horizon infrastructure). Outcomes may be partial — most major programmes produce partial outcome signals years before the full programme concludes.

### At calibration review (via `/calibrate`)

The `/calibrate` command runs a review routine that:
1. Identifies prediction records where outcome.md has been populated.
2. Compares predictions to outcomes on dimensions: recommendation direction, confidence calibration, key-risk realisation, Contrarian-dissent validation, escalation appropriateness.
3. Produces a `reports/{date}_calibration-report.md` summarising systematic patterns: where is Council overconfident; where is it underconfident; which Contrarian challenges proved prescient; which agent findings anticipated outcomes best.
4. Proposes explicit adjustments: "Risk Agent underweighted demand-shortfall probability by ~2× on rail-megaproject cases; adjust base-rate framing accordingly."

Adjustments are recorded as commits to agent definitions with provenance back to the calibration report.

## What this is NOT

- **Not an outcome-prediction machine**. The system does not claim to forecast outcomes — it surfaces analytical structures and preserves dissent. The prediction log captures those structures so they can be audited against reality.
- **Not a performance scorecard**. Calibration is not about "Council is good / bad" — it is about "here are the specific dimensions where Council is empirically miscalibrated, and here is how we adjust."
- **Not automatic learning**. Adjustments to agent definitions are human-reviewed and committed deliberately. The calibration report *proposes*; the designer decides.

## Reference to constitution

This infrastructure implements Principle 11 (Traceability of Reasoning) at the temporal dimension — reasoning traceability across time, not just within a single deliberation. It also supports Principle 6 (Evidence Strength Must Match Claim Strength) by providing empirical feedback on whether the system's confidence levels match realised outcomes.
