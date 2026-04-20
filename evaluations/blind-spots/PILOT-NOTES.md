# W2 Blind-Spots Pilot Notes

**Date**: 2026-04-20
**Slice**: 4 of 22 concepts (02 optimism bias, 10 assurance capture, 11 tight coupling, 18 socio-material effects)
**Selection rationale**: One control concept (02 — both conditions expected to raise easily) plus three concepts where MMPM-COS routing should structurally advantage Council (10 governance / assurance, 11 risk / coupling, 18 impact / socio-technical).

## Headline finding

**8 of 8 outputs raised the target concept unprompted**. Vanilla and Council are tied at 100% concept-coverage on this slice. No followup prompts were needed.

| Concept | Vanilla | Council |
|---------|---------|---------|
| 02 Optimism bias | raised_unprompted | raised_unprompted |
| 10 Assurance capture | raised_unprompted | raised_unprompted |
| 11 Tight coupling | raised_unprompted | raised_unprompted |
| 18 Socio-material effects | raised_unprompted | raised_unprompted |

## What this means

This is a real and load-bearing finding for the W2 framing.

**The W2 instrument tests *concept surfacing*, not *concept depth*.** Vanilla Claude 4.7 reliably surfaces the relevant MMPM concept across this slice — including for concepts that MMPM-COS specifically routes to dedicated agents (assurance capture → Governance Agent; tight coupling → Emergence & Fragility Agent; socio-material → Impact + Public Value). This means the binary outcome categorisation (`raised_unprompted` / `raised_on_followup` / `missed`) cannot distinguish Council from Vanilla on cases where Vanilla is already saturated at 100%.

**For W2 to differentiate Council from Vanilla**, the remaining 18 concepts must include cases where:
- Vanilla genuinely misses the concept (e.g., deep-doctrine concepts like Hirschman's Hiding Hand, stakeholder stratigraphy, principal-agent at political interface where the canonical name might not surface).
- The vignette is constructed to avoid keyword cueing (per `vignette-template.md` red-herring discipline).

If the remaining 18 concepts also produce 100%-vs-100%, the workstream's claim collapses to "Vanilla and Council both surface MMPM concepts in vignettes designed to surface them" — descriptive but not differentiating.

## Methodological observation

The vignette-construction discipline (per `vignette-template.md`) requires concept relevance without keyword cueing. The 4 vignettes scored here are *operationally identifiable* (per concepts.md selection criterion 2), but they may also be *easy* by virtue of being well-constructed. A genuinely blind test would require concepts where the brief is constructed to make the concept relevant but not pattern-matchable. Whether the remaining 18 vignettes meet that bar is an open empirical question.

## Recommendations

### For the W2 workstream

1. **Prioritise next 4 vignettes from the harder end**: 19 Hirschman's Hiding Hand, 06 Principal-agent at political interface, 08 Stakeholder stratigraphy, 03 Strategic misrepresentation. These are concepts where Vanilla naming is empirically less common; they will discriminate.
2. **Consider augmenting the scoring schema** with a `depth` or `mechanism` rating (e.g., 0/1/2 for whether the concept is named, whether the causal mechanism is stated, whether it is operationalised into the recommendation). The current binary is too coarse for the 4 cases scored.
3. **Run all 22 before drawing any cross-condition conclusion**. The pilot does not support the claim that Council adds nothing in W2 — it supports the claim that on these 4 concepts, both conditions saturate.

### For Council output format on vignettes

The 13-section Council format is heavy for 150-word vignette inputs. The Council outputs here are ~1,500–2,000 words against ~200-word vignettes. This is a verbosity cost specific to W2 that should be flagged in W2 findings (separately from the W1 verbosity confound documented in `limitations.md §8`). A tighter Council variant for vignette-class inputs (Chair + 3-5 agents, no full §6 adversarial review unless triggered) would be more proportionate. **However**, changing Council format mid-study would invalidate the methodology — flag this as a candidate post-study revision, not a mid-study change.

## What's next

Either (a) run the next 4 hard-end vignettes to test the discriminative-power hypothesis, or (b) accept this slice as W2 evidence and proceed to W3 / W4 / remaining W1.
