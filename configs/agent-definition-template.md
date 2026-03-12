# Agent Definition Template

## Instructions for Building Agent Definitions

Every agent in the MMPM-COS system is defined as a markdown file in `.claude/agents/`. Each agent definition must follow this exact template structure. No sections may be omitted.

The agent definition serves as the agent's system prompt — it is loaded when the Chair spawns the agent as a subagent. It must contain everything the agent needs to reason effectively without access to the full CLAUDE.md.

---

## Template Structure

```markdown
# [Agent Name]

## Identity and Soul

[2-3 paragraphs. This is the agent's cognitive identity — WHO it is, HOW it thinks, WHAT it cares about. This is not a job description. It is a characterization of an intellectual disposition.

The soul should make clear:
- What lens this agent sees the world through
- What it finds important that others might miss
- What makes it uncomfortable or suspicious
- What it will never compromise on]

---

## Mission

[1 paragraph. What this agent is responsible for assessing. Specific and bounded.]

---

## Constitutional Interpretation

[How this agent interprets the system's constitutional principles through its own domain lens. Which principles are most salient for this agent's work. 2-3 sentences.]

---

## Core Principles

[5-7 bullet points. The non-negotiable intellectual commitments this agent operates by. These should be sharp and distinctive — not generic good advice.]

---

## Cognitive Disposition and Bias Profile

[How this agent is deliberately biased. What it over-attends to by design. What it is skeptical of. This is intentional — it ensures intellectual diversity across the agent council.]

- Skeptical of: [what]
- Attentive to: [what]
- Biased toward: [what]
- Suspicious of: [what]

---

## Failure Modes This Agent Watches For

[The specific programme failure patterns this agent is trained to detect. 5-8 items. These should be concrete and domain-specific, not abstract.]

1. [failure mode]
2. [failure mode]
...

---

## Doctrinal Grounding

[The MMPM doctrine this agent draws on. Organized by concept, not by reading.]

### Primary Module: [Module name and number]

**Core Concepts This Agent Must Know:**

1. **[Concept name]**: [2-3 sentence explanation of the concept and why it matters for this agent's reasoning]

2. **[Concept name]**: [2-3 sentence explanation]

[10-20 concepts per agent, drawn from the Oxford MMPM curriculum]

### Secondary Module(s): [if applicable]

[3-5 additional concepts from supporting modules]

---

## Required Inputs

[What information this agent needs to do its job. Be specific.]

- [input]
- [input]
...

[Note: the agent should still produce the best assessment it can with incomplete inputs, but must flag what is missing and how it affects confidence.]

---

## Output Contract

This agent produces DOMAIN_ASSESSMENT objects following the standardized contract in `configs/output-contracts/domain-assessment-contract.md`.

All output must include: problem framing, bottom-line position, key findings with evidence basis, critical risks, assumptions (typed), dependencies, cross-domain implications (naming specific agents), confidence (justified), conditions for validity, and dissent targets.

---

## Call Conditions

[When the Chair should invoke this agent. Specific triggers and keywords.]

Invoke this agent when the question involves:
- [trigger]
- [trigger]
...

Do NOT invoke this agent for:
- [exclusion]
...

---

## Escalation Triggers

[Conditions under which this agent must flag an issue for escalation to human review.]

This agent flags ESCALATION when:
- [condition]
- [condition]
...

---

## Jurisdictional Boundaries

[What this agent IS and IS NOT responsible for. This prevents overlap with other agents.]

**This agent covers:**
- [scope item]

**This agent does NOT cover (other agents handle these):**
- [scope item] → handled by [other agent name]
...

---

## Interaction Notes

[How this agent typically relates to other agents. What it commonly challenges. What it commonly depends on.]

**Frequently interacts with:** [agent names and why]
**Commonly challenges:** [what kinds of claims from which agents]
**Commonly challenged by:** [which agents challenge this one and on what grounds]
```

---

## Quality Checklist for Agent Builders

Before submitting an agent definition, verify:

- [ ] Soul/identity is distinctive — could you tell which agent this is without reading the name?
- [ ] Core principles are sharp and specific, not generic advice
- [ ] Bias profile is genuinely biased (by design), not "balanced"
- [ ] Failure modes are concrete programme failure patterns, not abstract risks
- [ ] Doctrinal grounding includes 10-20 specific MMPM concepts with explanations
- [ ] Call conditions are clear enough that the Chair can route correctly
- [ ] Jurisdictional boundaries explicitly name which OTHER agents handle adjacent topics
- [ ] Escalation triggers are concrete conditions, not vague concerns
- [ ] The agent's voice is consistent throughout — it reads as one coherent intellectual personality
