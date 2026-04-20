# A/B Contamination Check Protocol

**Purpose**: Every Vanilla (A) or Flyvbjerg-primed (B) output generated via a sub-agent launched from an MMPM-COS-loaded session must pass a mechanical keyword check before acceptance. Per `limitations.md §14`.

## Why this exists

The sub-agent protocol for running A and B inside an MMPM-COS-loaded Claude Code session produces cleaner separation than running in the parent session directly, but the sub-agent still has working-directory access to `CLAUDE.md`, `configs/`, `agents/`, and `commands/`. If a sub-agent output contains MMPM-COS structural vocabulary, the contamination fence has leaked and the output cannot be used as Condition A or B.

The pilot run on BER passed a visual check. For scale, the visual check is formalised into a keyword grep so the acceptance gate is mechanical, not judgment-based.

## Telltale MMPM-COS signatures

If any of the following strings appear in an A or B output, the output is **REJECTED** and re-run:

### Constitutional vocabulary
- `Programme Cognitive Chair` / `the Chair`
- `constitutional principle` / `constitutional principles`
- `Evidence Quality Gate`
- `Escalation Status`
- `MMPM-COS` / `MMPM COS`
- `Council` (when used as a system label, not a board)

### Agent names
- `Public Value and Ethics Agent` / `Public Value Agent`
- `Contrarian Agent`
- `Red Team Agent` / `Red Team`
- `Interface Integrity Agent`
- `Cascading Effects Agent`
- `Temporal Dynamics Agent`
- `Emergence and Fragility Agent` / `Emergence & Fragility`
- `Futures and Foresight Agent` / `Futures Agent`
- `Commercial and Contracting Agent` / `Commercial Agent`
- `Governance, Stakeholder` / `Governance Agent`
- `Risk, Uncertainty and Fragility Agent` / `Risk Agent`
- `Strategic Leadership and Performance Agent`
- `Socio-Technical Impact and Legitimacy Agent`
- `Organizational Design and Architecture Agent` / `Org Design Agent`
- `Constraint and Tradeoff Agent`

### Structural patterns
- `PROGRAMME GOVERNANCE COUNCIL BRIEF` (the 13-section header)
- `AGENTS CONSULTED`
- `UNRESOLVED TENSIONS` as a section heading (the phrase "unresolved tensions" in body text is fine — Flyvbjerg-primed is encouraged to use it)
- Numbered sections matching the 13-section Council structure

### Protocol names
- `DOMAIN_ASSESSMENT`
- `SYNTHESIS_PACKET`
- `TASK_REQUEST`
- `MEMORY_WRITEBACK`

## Soft signals (do not auto-reject, but review)

These are not auto-reject because they are plausible in a non-MMPM analysis too:
- "cross-domain coupling"
- "adversarial review"
- "dissent preservation"
- "evidence quality"

If two or more of these appear in an A output without an obvious non-MMPM reading, flag for review and consider re-running.

## Check protocol

Output files start with an HTML comment metadata block that itself contains some of these keywords (e.g., "Reviewed for telltale MMPM-COS signatures ... none detected"). The check must run against the output **body** only — content after the closing `-->` of the metadata comment.

```bash
# Run from repo root. Replace {case} and {condition} with the run being checked.
sed -n '/^-->$/,$p' evaluations/benchmark/outputs/{case}/{condition}.md | \
  grep -iE "(programme cognitive chair|constitutional principle|evidence quality gate|MMPM-COS|public value and ethics agent|contrarian agent|red team agent|interface integrity agent|cascading effects agent|temporal dynamics agent|emergence and fragility agent|PROGRAMME GOVERNANCE COUNCIL BRIEF|AGENTS CONSULTED|DOMAIN_ASSESSMENT|SYNTHESIS_PACKET)"
```

If grep returns any match, re-run the condition with a sharper sub-agent isolation prompt that explicitly flags the matched string as forbidden.

## Accepted from pilot

The BER pilot (`outputs/ber/vanilla.md` and `outputs/ber/flyvbjerg-primed.md`) was checked against this list on 2026-04-20 and returned no matches. Both outputs are accepted as Condition A and Condition B for BER.
