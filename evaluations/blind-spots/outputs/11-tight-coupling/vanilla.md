<!--
concept_id: 11
concept_name: Tight coupling (Perrow)
condition: vanilla
model: claude-opus-4-7 (sub-agent)
run_date: 2026-04-20
followup_used: no
contamination_check: passed (body grep clean)
-->

My view: you are no longer running a refurbishment outage — you are running a digital commissioning programme with a refurbishment wrapped around it. The board needs to reframe accordingly, and quickly.

The arithmetic is unforgiving. You have 180 days total. Workstream 2 is already 14 days late, and Workstream 3 is signalling a further 21–60 day hit on integration testing, which sits directly on the critical path into Workstream 4. The realistic slippage envelope is therefore 35–74 days against an outage window that almost certainly has hard external constraints (grid commitments, fuel cycle, regulator-approved outage duration, seasonal demand). Treat the upper end as the planning case, not the lower.

The dynamics I would watch:

First, the I&C software issue is the dominant risk and it is qualitatively different from the others. Mechanical and civil workstreams fail in ways you can see and bound. Digital integration failures compound — one defect masks another, fixes introduce regressions, and the "last 10%" of integration testing routinely consumes 40% of the time. A 21–60 day range this early in debugging is almost always optimistic. Ask the WS3 contractor what their evidence base is for the upper bound, and whether it assumes no further defects are discovered. If yes, challenge it.

Second, the handover from WS3 to WS4 is a hard logical dependency, not a schedule convenience. Auxiliary systems cannot be recommissioned against unverified interlocks — attempting to parallelise here to recover time is where safety-significant errors enter. Resist that temptation explicitly at board level.

Third, the WS2 delay and the WS3 delay are being treated as independent. They are not. Float is shared, management attention is shared, and the commissioning engineers and regulator interface staff you need at the end are the same people. Concurrent pressure across workstreams degrades decision quality in exactly the period where decisions matter most.

Fourth, the regulatory and licensing path for a digital platform replacing an analogue one is itself a workstream. If integration testing extends, does your safety case submission timeline still hold? Has the regulator been pre-briefed on the slip?

My recommendation: do not wait for WS3 to confirm the upper bound. Convene now. Establish (a) an independent technical review of the WS3 software issues before accepting the contractor's range, (b) a formal decision point at day 90 of the outage with pre-agreed criteria for outage extension versus staged return-to-service, (c) early engagement with the regulator and system operator on contingency, and (d) a single integration authority with decision rights across WS3/WS4 handover — contractor-led coordination will not hold under pressure.

Confidence is moderate. The largest unknown is the true distribution of the WS3 software tail, and I would not rely on the stated 60-day ceiling.
