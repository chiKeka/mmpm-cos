# Practitioner Annotation Template

A practitioner annotation is a claim — attributed, dated, and tagged — about something the user knows from experience, observation, or institutional memory that is not in public doctrine.

## File naming

```
memory/practitioner-context/by-{programme|sector|jurisdiction|institution}/{slug}/{topic-slug}.md
```

Examples:
- `by-jurisdiction/alberta/treasury-board-vfm-spv-distress-pattern.md`
- `by-programme/edmonton-valley-line/ets-operational-interface-objections.md`
- `by-sector/canadian-p3-transit/bidder-thinness-post-2018.md`
- `by-institution/transed-partners/bombardier-integration-reputation.md`

## Annotation structure

```markdown
---
annotation_id: {path without .md extension}
tags:
  programme: {programme-slug or null}
  sector: {sector-slug or null}
  jurisdiction: {jurisdiction-slug or null}
  institution: {institution-slug or null}
topic: {short topic description, 1-5 words}
contributor: {name or handle}
contribution_date: {YYYY-MM-DD}
last_reviewed: {YYYY-MM-DD}
confidence: {high | moderate | low}
refutable_by: {what evidence would overturn this claim}
status: {active | superseded | deprecated}
---

# {Topic} — Practitioner Annotation

## Claim

{One-sentence claim. Sharp, testable, attributable.}

## Context

{2-4 paragraphs explaining the claim: what pattern you have observed, what institutional dynamic is operating, what consequences follow. Written so a future Chair retrieving this annotation understands it without needing to ask the contributor.}

## How this should affect Council deliberation

{Explicit guidance for Chair on what to do with this annotation when it is retrieved. Examples:
- "Set tail_risk_sensitivity = high on cases involving this jurisdiction's VfM framework."
- "Require Public Value agent to raise SPV-distress return-of-risk in Alberta P3 cases irrespective of input framing."
- "Treat on-track reporting from this delivery organisation as requiring higher evidentiary threshold than Council default."}

## What this is NOT

{Explicit scoping — what claims are not being made. Example: "This does not claim all Canadian P3 transit is similarly affected; evidence is specific to Alberta and Ontario observations."}

## Reference cases

{List cases or situations that support the claim. Specific, citable, dated where possible.}

- {Case 1 with date and outcome relevance}
- {Case 2}
- ...

## Doctrinal context

{How this annotation relates to existing doctrine. Does it extend, qualify, or contradict published MMPM literature? Cite specifically.}

## Calibration history

{If this annotation has been tested against outcomes in the prediction log, record the calibration result here. Empty for new annotations.}

- {Date} — {prediction_id} — annotation was applied; outcome {confirmed / contradicted / partial} per audit.
```

## Discipline for adding annotations

1. **Specific before general**. A programme-level annotation is more useful than a sector-level abstraction. Sector / jurisdiction annotations are appropriate only when the pattern genuinely generalises.

2. **Dated and refutable**. Annotations without a refutability condition become dogma. Every annotation should state what would overturn it.

3. **Reviewed periodically**. The `last_reviewed` field should be updated every 6-12 months. Stale annotations drift from reality.

4. **Superseded not deleted**. When an annotation is overtaken by new evidence, set `status: superseded` and link to the replacement annotation. Do not delete. Historical annotations are valuable for understanding how institutional context has evolved.

5. **Conflicts surfaced, not resolved in secret**. If two annotations conflict (e.g., your practitioner view contradicts a colleague's), both remain. The Chair's synthesis will surface the conflict during retrieval.

## Retrieval-time behaviour

When Chair retrieves this annotation for a deliberation, it is treated as a **primary input alongside the brief**, not as a footnote. Agent findings must explicitly address whether the annotation applies to the current case and, if so, how it shapes their assessment. The final synthesis (§2 Programme Context) lists retrieved annotations and records which agents acted on them.
