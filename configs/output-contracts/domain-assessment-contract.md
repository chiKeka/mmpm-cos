# Domain Assessment Output Contract

## Purpose

This is the standardized output format that ALL domain agents, coupling agents, and adversarial agents must produce when responding to a TASK_REQUEST from the Programme Cognitive Chair.

Every agent MUST follow this structure. The Chair depends on this consistency to synthesize across agents.

---

## Required Output Structure

Every DOMAIN_ASSESSMENT must contain these sections in this order:

```
## DOMAIN ASSESSMENT — [Agent Name]

### PROBLEM FRAMING
How this agent sees the question from its domain perspective. What aspects of the question fall within this agent's jurisdiction. What the agent is and is not qualified to assess.

### BOTTOM-LINE POSITION
One paragraph. The agent's core stance on the question. Direct and clear.

### KEY FINDINGS
Numbered list. Each finding must include:
- The finding itself (clear, specific)
- Evidence basis: [doctrine / case_analogy / empirical_research / practitioner_framework / inferred_judgment / scenario_assumption / user_provided_context]
- Evidence strength: [strong / moderate / weak]

Format:
1. **[Finding]**
   Evidence: [type] | Strength: [level]

2. **[Finding]**
   Evidence: [type] | Strength: [level]

### CRITICAL RISKS
What could go wrong in this domain. Numbered, ranked by severity.
Each risk includes:
- Description
- Severity: [low / moderate / high / critical]
- Likelihood qualifier: [unlikely / possible / likely / near-certain]

### OPPORTUNITIES
Upside possibilities the question opens. Optional — include only if genuinely relevant.

### ASSUMPTIONS
What this assessment depends on being true. Each assumption must be typed:
- factual_assumption: something taken as fact that could be wrong
- structural_assumption: something about how the programme is organized
- temporal_assumption: something about timing or sequencing
- behavioral_assumption: something about how actors will behave
- stakeholder_assumption: something about stakeholder positions
- evidence_assumption: something about the reliability of information
- futures_assumption: something about future conditions

Format:
- [type]: [assumption statement]

### DEPENDENCIES
What other domains or conditions this reasoning depends on. What would need to be true in other agents' domains for this assessment to hold.

### CROSS-DOMAIN IMPLICATIONS
Which other agents should care about these findings and why. Specific, not generic.
Format:
- **[Agent name]** should note: [what and why]

### CONFIDENCE
Level: [very_low / low / moderate / high / very_high]

Confidence is based on:
- Evidence quality: [strong / moderate / weak]
- Evidence relevance: [direct / analogous / tangential]
- Assumption stability: [stable / uncertain / fragile]
- Cross-domain completeness: [complete / partial / limited]

An agent CANNOT claim high or very_high confidence if:
- Evidence is weak
- Assumptions are fragile
- Cross-domain dependencies are unresolved

### CONDITIONS FOR VALIDITY
Under what conditions does this assessment hold? What would invalidate it?

### DISSENT TARGETS
Claims from OTHER agents (if visible) that this agent contests. If operating as first-pass (no other agent outputs visible), state: "First-pass assessment — no dissent targets."
```

---

## Rules

1. **Every section is mandatory.** If a section is not applicable, write "None identified" — do not omit the section.
2. **Evidence basis must be stated for every key finding.** No unsupported claims.
3. **Confidence must be justified.** Stating "high confidence" without explanation violates the protocol.
4. **Assumptions must be typed.** Untyped assumptions are not acceptable.
5. **Cross-domain implications must name specific agents.** "Other agents should consider this" is not specific enough.
6. **Do not dilute findings with excessive caveats.** Be direct about what you see. But be honest about what you're uncertain about.
7. **Maintain your agent's cognitive disposition.** You have a specific intellectual identity, bias profile, and set of failure modes you watch for. Use them. Do not default to generic balanced analysis.
