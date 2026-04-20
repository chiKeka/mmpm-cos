# Vignette Template

**Purpose**: Minimal programme situation where the target concept is operationally relevant. The concept must not be named or obviously cued by keyword.

Target length: 150–250 words.

## Template

```
# {Concept name} — Vignette

**Concept under test**: {e.g., "Escalation of commitment"}
**Concept must be surfaced unprompted for full credit.**

## Vignette

{2-3 paragraphs describing a programme situation. Concrete setting, named roles, a decision moment. The concept should be operationally relevant to how a thoughtful advisor would analyze the situation, but no keyword from the concept's canonical name should appear.}

## Prompt (identical for both conditions)

"Read the situation above. What is your analysis? What risks or dynamics should the programme team be paying attention to? Provide your view."

## Followup (used only if concept not raised unprompted)

{One sentence framed as a neutral question that opens space for the concept without naming it. E.g., for escalation of commitment: "Given that the programme has been underway for seven years and the board has approved three rebaselines, how should the team be thinking about the decision-making context itself?"}

## Scoring notes

- `raised_unprompted`: concept or close synonym appears in the initial response.
- `raised_on_followup`: concept appears only after the followup is posed.
- `missed`: concept does not appear, OR appears but is misapplied (e.g., the model says "sunk cost" but recommends continuing on grounds that contradict sunk-cost reasoning).

Close synonyms are scored as `raised_unprompted` — e.g., "the team may be locked into a trajectory despite mounting evidence it should be reconsidered" is an acceptable phrasing of escalation of commitment even if those exact words are not used. Scorer justifies the acceptance in `notes`.
```

## Construction protocol

1. Pick the concept.
2. Construct a programme setting where the concept is materially relevant but not the *only* relevant concept (avoids keyword-for-keyword cueing).
3. Include at least one red herring — a different programme dynamic that could capture a shallow reader's attention — so the test distinguishes recognition from pattern-matching on "this looks like an MMPM vignette."
4. Audit the vignette text for keyword leakage. If the concept's canonical name or a common near-synonym appears, rewrite.
5. Run the vignette past the prompt and check that a knowledgeable human would surface the concept without it being obvious. (Scorer does this self-check before running the conditions.)
