# MMPM-COS Memory System

## Purpose

The memory system transforms MMPM-COS from a stateless question-answering engine into a system that learns from its own decisions and from practitioner experience.

## Memory Types (MVP)

### 1. Decision Log (Episodic Memory)
**Location**: `memory/decisions/`
**Format**: One markdown file per decision, named `YYYY-MM-DD-[short-topic].md`

Every Council, Exploration, and Analyst session produces a decision record:

```markdown
# Decision Record: [Topic]

## Metadata
- Date: [date]
- Mode: [Council / Exploration / Analyst]
- Problem type: [classification]
- Session context: [programme name/description if provided]

## Parameters
[Active parameter settings for this session]

## Question
[The original question]

## Agents Invoked
[List of all agents that participated]

## Key Findings
[Summary of the most important findings across agents]

## Recommendation
[The system's recommendation]

## Key Assumptions
[The most important assumptions the recommendation depends on]

## Dissent and Unresolved Tensions
[Material disagreements that persisted — which agents, what they disagreed about]

## Confidence
[Level and reason]

## Escalation Status
[None / Recommended / Required — with reason]

## Practitioner Notes
[Any corrections or annotations the user provided during or after the session]
```

### 2. Practitioner Context Store
**Location**: `memory/practitioner-context/`
**Format**: One markdown file per programme or topic, named `[programme-name].md`

Stores user-provided experiential knowledge:

```markdown
# Practitioner Context: [Programme/Topic Name]

## Programme Description
[Type, sector, geography, scale, phase]

## Context Notes
[User-provided context about the programme environment]

### [Date] — [Topic]
[Specific practitioner insight, correction, or annotation]

### [Date] — [Topic]
[Another insight]
```

## Write Policy

### ALWAYS write:
- Council mode sessions (full deliberation)
- Exploration mode sessions (scenario analysis)
- Any session where the user provides practitioner corrections
- Any session where agents flagged escalation

### WRITE if useful:
- Analyst mode sessions that produced substantive findings
- Sessions with notable agent disagreement

### DO NOT write:
- Tutor mode sessions (doctrine explanation — no decision made)
- Brief mode sessions (just reformatting prior decisions)
- Trivial or exploratory exchanges

## Read Policy

### When the Chair should search memory:
- At the START of any Council or Exploration session — check if there are prior decisions on this programme or topic
- When a user references a past session — "remember when we analyzed..."
- When the question touches a programme for which practitioner context exists

### How to search:
- Search `memory/decisions/` for topic keywords
- Search `memory/practitioner-context/` for programme name
- Surface relevant past decisions in the Chair's context-building step

## Deferred (Future Phase)

These are NOT in the MVP but are designed for:
- **Reflective memory**: Tracking which assumptions held and which broke (requires outcome data from users)
- **Cross-programme pattern detection**: Finding recurring themes across multiple programmes
- **Agent accuracy scoring**: Tracking which agents were most/least accurate over time
