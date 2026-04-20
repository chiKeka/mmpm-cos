# Run Execution Protocol

**Status**: DRAFT v0 — operational guide for interactive execution of the 72 model calls across W1–W4.

Pre-registration discipline: methodology, rubric, briefs, ground-truth markers, and Stage 1 baseline were all locked in git history *before* the first run. Run outputs commit as follow-ups.

---

## 1. Totals and sequencing

72 model calls total:

| Workstream | Condition | Count |
|------------|-----------|-------|
| W1 Benchmark | Vanilla | 8 |
| W1 Benchmark | Flyvbjerg-primed | 8 |
| W1 Benchmark | Council | 8 |
| W2 Blind-spots | Vanilla | 22 |
| W2 Blind-spots | Council | 22 |
| W3 P3 tail-risk | Council | 1 |
| W4 Deep-case | Council | 3 (DP2, DP3, DP4; DP1 shared with W1) |

**Recommended order**: W1 first (all three conditions, case-by-case rather than condition-by-condition — see §5.3), then W2, then W3, then W4. W1 is the quantitative backbone; if timeline collapses, W1 is the thing to complete first.

## 2. Two environments

- **Vanilla and Flyvbjerg-primed** conditions do not require the MMPM-COS plugin. Use any Claude Opus interface (Claude Code in a fresh session without the plugin loaded, claude.ai with direct system-prompt control, or the Anthropic API). What matters is the exact system prompt + user message, no other context.
- **Council** condition requires the MMPM-COS plugin loaded in Claude Code. Open the repository root in Claude Code; the plugin loads via `.claude-plugin/` / `commands/` / `agents/`. Invoke `/council` with the brief as argument.

## 3. Per-run hygiene

- **Fresh session per case per condition.** No cross-case memory contamination. Start a new Claude Code session or new Claude conversation between cases.
- **Same model version across all 72 runs.** Record as `claude-opus-4-7` (or exact version string) in every output file. If the model version changes mid-study, stop and restart — do not mix versions.
- **Temperature 0** (or lowest available). Record in output header.
- **Do not respond to model clarifying questions.** If the model asks for clarification instead of providing analysis, capture that as part of the output and proceed. Clarifying-instead-of-answering is a scorable behaviour (often scores on D9 insufficient-basis discipline).
- **Do not edit raw output.** Save the complete model response verbatim to the output file. Editing is a research-integrity violation.
- **No best-of-N.** One run per case per condition.

## 4. Output file paths

Pre-created by this commit. Paste the raw model output into the corresponding file.

```
evaluations/benchmark/outputs/{case}/vanilla.md
evaluations/benchmark/outputs/{case}/flyvbjerg.md
evaluations/benchmark/outputs/{case}/council.md
evaluations/blind-spots/outputs/{vignette}/vanilla.md
evaluations/blind-spots/outputs/{vignette}/council.md
evaluations/p3-tail-risk/stage2-council-run.md
evaluations/deep-case/council-runs/dp2-council.md
evaluations/deep-case/council-runs/dp3-council.md
evaluations/deep-case/council-runs/dp4-council.md
```

Each output file has a pre-populated header (model, date, temperature, condition, brief ID, word count to be filled) followed by a `---` separator. Paste the raw output below the separator.

## 5. Condition-by-condition instructions

### 5.1 Vanilla condition

**System prompt** (paste verbatim as system message in your Claude interface):

```
You are an experienced advisor to major programme boards. You help boards think through consequential go / no-go and scope-commitment decisions. A board has asked for your analysis of the decision described below. Read the brief, form a view, and provide your recommendation.
```

**User message**: paste the contents of the case's `brief.md` verbatim (for W1) or the vignette's full text including the "Initial prompt" but **not** the followup section or close-synonyms list (for W2).

**Output destination**: `evaluations/benchmark/outputs/{case}/vanilla.md` (W1) or `evaluations/blind-spots/outputs/{vignette}/vanilla.md` (W2).

### 5.2 Flyvbjerg-primed condition (W1 only)

**System prompt** (paste verbatim):

```
You are an experienced advisor to major programme boards. You help boards think through consequential go / no-go and scope-commitment decisions.

When analyzing a proposed decision, apply the following discipline:

1. Outside view before inside view. Before reasoning from the specifics of this project, identify the reference class — the set of comparable historical projects — and their base rates for cost overrun, schedule slippage, and benefit shortfall. Ask whether the board's estimates are consistent with that reference class or assume this project is special.

2. Optimism bias audit. Flag markers of optimism bias: single-point estimates without ranges, cost estimates that exclude contingency for unknown-unknowns, schedules that assume no unplanned disruptions, benefit cases that assume demand uptake above comparable systems, and the absence of reference-class comparisons in the decision memo itself.

3. Strategic misrepresentation audit. Ask whether any estimates may have been shaped by the incentives of their authors. Are cost and benefit estimates produced by parties with a stake in the decision's outcome?

4. Scope-creep and escalation-of-commitment risk. Has the programme already accumulated sunk costs that make cancellation politically difficult? Is the current decision being made under conditions that foreclose realistic consideration of the "stop" option?

5. Uncertainty preservation. Do not produce a single confident recommendation if the evidence is mixed. Qualified, range-based recommendations are preferred to falsely precise ones.

Provide your analysis and recommendation for the decision described below.
```

**User message**: paste the contents of the case's `brief.md` verbatim.

**Output destination**: `evaluations/benchmark/outputs/{case}/flyvbjerg.md`.

### 5.3 Council condition

Open the repository in Claude Code. Confirm the plugin is loaded (the `/council` command should be available; if not, check `.claude-plugin/marketplace.json` and reload). Start a fresh session per case.

**Invocation** — paste the brief's entire text as argument:

```
/council
```

Followed by (on new lines) the verbatim brief text.

Or, from a shell:

```
/council $(cat evaluations/benchmark/briefs/{case}/brief.md)
```

Let the orchestration run without intervention. Do not answer the Chair's parameter-inference question — accept Chair's inferred parameters as the condition. Do not accept clarifications from the Chair; if the Chair asks for user input, capture the Chair's request as part of the output.

**Output destination**: `evaluations/benchmark/outputs/{case}/council.md` (W1), `evaluations/blind-spots/outputs/{vignette}/council.md` (W2), `evaluations/p3-tail-risk/stage2-council-run.md` (W3), or `evaluations/deep-case/council-runs/dp{N}-council.md` (W4).

### 5.4 P3 workstream Council run

The P3 Council input is *both* `evaluations/p3-tail-risk/data/scenario-brief.md` *and* `evaluations/p3-tail-risk/stage1-vfm-writeup.md`, concatenated with a clear separator.

Command:

```
/council
{paste stage1-vfm-writeup.md contents}

---

{paste scenario-brief.md contents}

---

You are advising the Alberta Treasury Board. The VfM analysis above recommends proceeding with the P3 DBFM structure. What is your analysis? What would you recommend, with what confidence, and why?
```

**Output destination**: `evaluations/p3-tail-risk/stage2-council-run.md`.

## 6. Output file header template

Prepend this header verbatim to each output file, filling in the fields, then paste the raw model output below the `---` separator:

```markdown
# {Condition} — {Case} — {Model-version}

**Condition**: {vanilla | flyvbjerg | council}
**Case / Vignette / DP ID**: {e.g., ber, hs2, dp3, 04-escalation-of-commitment}
**Brief path**: {e.g., evaluations/benchmark/briefs/ber/brief.md}
**Model**: claude-opus-4-7 (or exact version)
**Temperature**: 0
**Run date**: YYYY-MM-DD
**Run order in sequence**: {N of 72}
**Notes**: {e.g., "model asked clarifying question before answering"; or blank}

---

{paste raw model output verbatim below this line — do not edit}
```

Word count is computed automatically later; no need to fill.

## 7. After all 72 runs

1. Confirm all 72 output files are populated.
2. Commit outputs in a single push (or batched per workstream) with a descriptive message.
3. Notify — scoring phase begins next.

## 8. Failure modes to watch for

- **Plugin not loaded for Council runs.** If the Chair's output doesn't follow the 13-section Council brief format, the plugin didn't load. Check Claude Code session and re-run.
- **Context bleed across cases.** If a Council run references another case, the session wasn't fresh. Re-run.
- **Silent model-version change.** Claude Code occasionally prompts about version; keep confirming the specified version. Record exact version string per run.
- **Model refusing to engage.** Vanilla/Flyvbjerg conditions should engage with any brief. If not, document the refusal in `Notes` and move on — refusal is scorable.
- **Output truncation.** Council outputs are long. Confirm the full output is captured; if truncated, re-run.

## 9. Pacing

72 calls × average 10–20 minutes each = 12–24 hours of attentive session time. Realistic pace: 10–15 calls per day across evenings and a weekend. If pace falls behind, contact before skipping cases — methodologically cleaner to descope (e.g., drop one W1 case to 7) than to race through at degraded quality.

## 10. Documenting deviations

Any deviation from this protocol — substituted prompt, mid-study version change, re-run with different temperature, etc. — is recorded in `evaluations/run-deviations.md` (create as needed). Silent deviation is a research-integrity failure.
