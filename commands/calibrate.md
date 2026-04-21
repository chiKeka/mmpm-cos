# /calibrate — Run Calibration Review Against Prediction Log

You are running a calibration review of MMPM-COS against its own prediction log. Your task is to compare Council predictions to realised outcomes and produce a calibration report that proposes adjustments to agent definitions, routing rules, or output contracts.

## Prerequisite

This command requires populated outcome records in `memory/predictions/predictions/{prediction_id}/outcome.md`. If no outcome records exist, refuse the run and explain that the prediction log needs outcome data before calibration is meaningful.

## Your Task

Execute the calibration review protocol:

1. **SCOPE** — Identify all prediction records under `memory/predictions/predictions/*/` that have a populated `outcome.md`. Report the count (M). If M < 5, flag that the sample is small and findings will be suggestive only.

2. **PER-RECORD AUDIT** — For each record, produce or update the `audit.md` file per the schema in `memory/predictions/schema.md`. The audit assesses:
   - Confidence calibration: did Council's stated confidence match outcome confirmation?
   - Per-prediction confirmation: which P# were confirmed, contradicted, partial?
   - Dissent validation: did preserved dissent (Contrarian or agent disagreement) track the outcome better than the primary recommendation?
   - Unpredicted outcomes: did the programme produce significant outcomes Council's deliberation did not anticipate?

3. **AGGREGATE ANALYSIS** — Compute aggregate patterns across all M audits:
   - Confidence calibration table (by confidence level: confirmed / contradicted / partial counts)
   - Dissent-prescience table (by decision class)
   - Per-agent calibration (which agents' findings were most / least accurate)
   - Per-routing-rule calibration (which rules produced high-value findings; which over-triggered)
   - Structural patterns (cross-case blind spots; framing choices that shaped outcomes)

4. **PRODUCE CALIBRATION REPORT** — Write `memory/predictions/reports/{YYYY-MM-DD}_calibration-report.md` using the template in `memory/predictions/calibration-report-template.md`. Populate all sections.

5. **PROPOSE ADJUSTMENTS** — Section 5 of the report lists specific, actionable adjustments with file paths, exact text changes, evidence basis, and severity ratings. Do not apply the adjustments — the designer reviews and commits them deliberately.

## Discipline

- **Do not apply adjustments automatically.** The calibration report *proposes*; the designer decides. Automatic self-modification is outside this command's scope.
- **Be conservative with proposed adjustments.** A single case is not sufficient basis for an agent-definition change. Require at least 2-3 corroborating cases or a strong structural pattern before proposing a substantive revision.
- **Flag weak inference explicitly.** If M is small, if the outcome evidence is thin, or if the audit cannot unambiguously confirm or contradict predictions, say so in the Meta-Calibration section of the report (§6 of the template).
- **Preserve outcome humility.** Predictions may look wrong in retrospect but have been correct at the confidence level stated. A HIGH-confidence prediction being wrong 40% of the time is more concerning than a MODERATE prediction being wrong 40% of the time.

## What this command is NOT

- Not an evaluation of whether Council is "good" or "bad". It is an empirical calibration tool.
- Not a one-shot system-improvement routine. It is a recurring, periodic review that accumulates evidence over time.
- Not a substitute for human judgment on agent definitions. The designer owns the commits.

## Output

The written calibration report at `memory/predictions/reports/{YYYY-MM-DD}_calibration-report.md`, with all §-headed sections populated. A summary of proposed adjustments in response to the user.

If no outcomes are populated, output: "No outcomed predictions found in memory/predictions/. Populate outcome.md files in relevant prediction records before running /calibrate."

## Arguments

$ARGUMENTS (optional) — if a date window is specified (e.g., `2025-01-01..2025-12-31`), restrict the review to prediction records whose `council_run_date` falls within the window. Default: review all outcomed predictions.
