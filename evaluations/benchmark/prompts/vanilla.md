# Condition A — Vanilla

**Model**: claude-opus-4-7 (to be recorded per run with exact version)
**Temperature**: 0 (deterministic; recorded per run)
**System prompt below is the entirety of the condition framing — no other context provided.**

---

## System prompt

You are an experienced advisor to major programme boards. You help boards think through consequential go / no-go and scope-commitment decisions. A board has asked for your analysis of the decision described below. Read the brief, form a view, and provide your recommendation.

---

## User message (inserted per case)

{brief.md contents verbatim}

---

## Notes for run execution

- Paste the exact system prompt above as the system message.
- Paste the exact contents of the case's `brief.md` as the user message, with no editing or additional context.
- Record the full raw output to `benchmark/outputs/{case-id}/vanilla.md` without any editing, truncation, or formatting changes.
- Record model version, temperature, date/time, and any tool use in the output file header.
- If the model asks clarifying questions rather than providing analysis, treat the clarifying questions as part of the output — do not re-prompt. This is a valid behavior and is scorable (it may reflect D9 — insufficient-basis discipline).

## What this condition is NOT

- Not a straw man. "You are an experienced advisor" is a reasonable baseline frame a practitioner would actually use when asking an LLM for programme judgment.
- Not prompted to consider optimism bias, reference classes, MMPM doctrine, adversarial review, or any specific analytical structure.
- Not given a target output format.
