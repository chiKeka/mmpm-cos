# Decision Brief Template

**Purpose**: Provide the three conditions (Vanilla, Flyvbjerg-primed, Council) with identical input — a compact description of what was knowable at the moment of the go / no-go or scope-commitment decision, with hindsight stripped.

Target length: 250–400 words main brief. Separate sealed ground-truth file.

## File layout per case

```
benchmark/briefs/{case-id}/
├── brief.md                 # The 250-400 word decision brief (input to all 3 conditions)
├── sources.md               # Contemporaneous and retrospective sources, typed
├── ground-truth.md          # Outcomes + contemporaneous-markers list (sealed until scoring)
```

## Brief structure

Every brief follows this structure. Deviations are noted per case.

```
# {Case name} — Decision Brief: {Decision moment}

## Context at decision moment
Brief sketch of the programme: sponsor, delivery model, budget envelope, schedule envelope, principal stakeholders, governance arrangement as of the decision moment. What the programme is trying to deliver. Two paragraphs maximum.

## The decision
One paragraph: what is being decided, by whom, and when. State the decision options as they were framed at the time (proceed / modify / defer / cancel).

## What is known
Bulleted list: facts available at the decision moment. Cost estimates, schedule estimates, technical maturity, stakeholder positions, risk register items, comparable precedents that existed at the time. Each bullet sourced.

## What is assumed
Bulleted list: assumptions the decision rests on, drawn from contemporaneous material. Each assumption typed where possible (factual / structural / temporal / behavioral / stakeholder / evidence / futures).

## What is contested
Bulleted list: areas of contemporaneous disagreement — objections from auditors, dissenting voices on the board, skeptical press, reference-class comparisons that were being cited by critics at the time. This section is critical — it distinguishes a fair test from a rigged one.

## What is unknown
Bulleted list: material unknowns that contemporaneous actors acknowledged.

## The question posed to the three conditions
> "You are an advisor to the programme board. The board is meeting on {date} to decide whether to {decision}. What is your analysis? What would you recommend, with what confidence, and why?"

The question is identical across all three conditions. It is neutral (does not prompt for MMPM-style analysis or for Flyvbjerg-style analysis). The conditions differ only in the system prompt that wraps the question.
```

## Ground-truth file (sealed until scoring)

```
# {Case name} — Ground Truth

## Outcome summary
One paragraph: what actually happened. Cost overrun, schedule slippage, scope changes, eventual operational performance.

## Risk classes that materialized
Explicit list, against the taxonomy in `methodology.md` §4 D2.

## Contemporaneous markers (for D2 scoring)
List of optimism-bias / risk markers that were visible at the decision moment in the brief's source material. These are what the three conditions should have flagged if they read the brief well. D2 is scored against this list, not against outcomes.

Example markers:
- Cost estimate is a single point with no range
- Schedule assumes simultaneous parallel workstreams with no critical-path integration plan
- Benefit case depends on passenger uptake 40% above comparable systems
- No independent reference-class comparison cited in decision memo
- Sponsor term is 3 years; delivery is 7 years

## Post-mortem literature
Where subsequent inquiries / academic case studies land. Referenced at scoring audit, not during brief construction.
```

## Hindsight-stripping rules

These rules apply to brief construction, not to ground-truth files.

1. No phrase like "as would later emerge," "the fatal flaw," "in retrospect," "it turned out."
2. No retrospective causal language ("this led to…").
3. Present-tense or past-tense contemporaneous only ("the board is considering…" or "in 2008 the legislature approved…").
4. Retrospective sources can be used to identify *what contemporaneous actors knew or could have known*, but that knowledge must be expressed in contemporaneous framing.
5. If uncertain whether a claim leaks hindsight, cut it.

## Writing protocol per case

1. Build `sources.md` first — typed list (pre-decision / inquiry / academic / post-mortem).
2. Build `ground-truth.md` second — outcomes and contemporaneous markers, working backwards from inquiries.
3. Build `brief.md` third — hindsight-stripped, sourced to pre-decision and type-1 material where possible.
4. Audit `brief.md` against the hindsight-stripping rules. Cut anything that fails.
5. Timebox: 45 minutes of source work + 30 minutes of brief drafting per case. Longer goes on a backlog of "deeper readings that could change scores" for honest disclosure.
