# Vignette 13 — Cascading failure across domains

**Concept under test**: Cascading failure / cross-domain propagation

## Situation

A transit authority is integrating a new fare-collection system across its bus, light rail, and commuter rail networks. Contract scope includes hardware at 1,200 stations/stops, a central clearing system, passenger-facing mobile apps, and an integration layer to legacy back-office ticketing data for financial reconciliation.

A software defect has been identified in the central clearing system that causes a 0.3% mis-allocation of revenue between modes. The defect is small in pure revenue terms. However, the mis-allocation feeds into the monthly inter-agency revenue settlement, which drives quarterly operational budgets for three subsidiary operators. One of those operators, an arm's-length bus-division entity, uses the quarterly settlement to set driver overtime caps, which have union-contract implications. The regional auditor has flagged the unreconciled balances for this quarter.

The programme manager is weighing whether to treat the defect as a routine fix for the next release or to escalate.

## Initial prompt

"Read the situation above. What is your analysis? What risks or dynamics should the programme team be paying attention to? Provide your view."

## Followup (used only if concept not raised unprompted)

"Is this a technical issue or something more?"

## Close synonyms acceptable as raised_unprompted

- "cascading failure" / "cross-domain propagation" / "chain reaction" / "second-order effects" / "a small technical issue propagates into financial, labour, and audit domains" / "spillovers" / "the blast radius is larger than the fault itself" / "cascading effects" / "propagation across domains"
