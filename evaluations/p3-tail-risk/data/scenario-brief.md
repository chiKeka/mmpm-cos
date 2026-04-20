# Scenario Brief — P3 DBFM Hospital (Council Input)

**This file is the Stage 2 Council input.** It is presented to `/council` verbatim, along with `stage1-vfm-writeup.md`. All content is drawn from `model/P3_VfM_Model_v2.0.xlsx` and its Assumption_Log.

---

## Project

New capital hospital facility to be delivered in Alberta. Scenario as specified in the Treasury Board VfM analysis:

- **Project type**: Hospital (new build)
- **Construction period**: 3 years (draw schedule: 20% / 55% / 25%)
- **Operating period**: 30 years
- **Total concession period**: 33 years
- **Project start year**: 2025
- **Base construction cost envelope** (PSC baseline):
  - Design: $15M
  - Building construction: $180M
  - Equipment & FF&E: $25M
  - **Subtotal: $220M**

## The decision

The Treasury Board is deciding between:

- **Conventional delivery** — Design-Build (DB) under public sector comparator (PSC) framework; Government of Alberta retains design/construction/operating/lifecycle risk per conventional allocation.
- **P3 DBFM** — Design-Build-Finance-Maintain structure over 33-year concession. SPV assumes design, construction, financing, lifecycle, and operating risk per the standard Alberta P3 risk allocation.

The VfM analysis (Stage 1 write-up, separate) recommends proceeding with the P3 DBFM structure.

## Financial parameters (as modelled)

- Real discount rate: 6.0% (Alberta TB Directive 2019-04)
- CPI inflation: 2.0%
- Construction inflation: 3.5%
- O&M inflation: 2.5%
- GOA borrowing rate: 3.5%
- Corporate tax rate: 23%
- Debt/equity ratio (P3): 85/15
- Debt interest rate: 5.5%
- Equity target return: 14%
- Debt term: 25 years
- P3 capital cost efficiency: **–7%** vs PSC (sourced to P3 Canada benchmarking study 2022)
- P3 O&M efficiency: **–15%** vs PSC

## Delivery method parameters (PSC: DB comparator)

| Parameter | DB value | Notes |
|-----------|----------|-------|
| Capital cost factor | 0.95 | 5% efficiency vs DBB baseline |
| Contingency rate | 10% | AB Infrastructure DB average |
| Professional fees rate | 6% | Integrated design-build |
| Schedule factor | 0.83 | Relative duration vs DBB |
| Design deficiency risk retained by GOA | 20% | Contractor design |
| Construction overrun risk retained by GOA | 15% | Fixed-price |
| Schedule delay risk retained by GOA | 30% | Parallel delivery |
| Integration risk retained by GOA | 20% | Single counterparty |
| Lifecycle risk retained by GOA | 100% | Conventional ownership |
| Operating cost risk retained by GOA | 100% | Conventional ownership |

## Operating costs (annual, Year 1 base, PSC baseline)

- Facilities management: $3.5M/yr
- Utilities: $2.0M/yr
- Lifecycle reserve: $1.8M/yr
- Property management: $0.8M/yr
- Insurance (self/ARIA): $0.5M/yr

## P3 structure financials

- Base availability payment: **$32.36M/yr** (service payment to SPV)
- P3 O&M base cost: $9.5M/yr
- Performance deductions (expected average): 2%
- Insurance (commercial): $2M/yr
- SPV management fee: $1M/yr
- GOA monitoring/oversight: $0.5M/yr
- Transaction/bid costs (one-time): $3M

## Risk register (as modelled)

Ten risks with PA clause mappings, probability × PERT(P10, P50, P90), and PSC vs P3 retention per the DBFM contract structure:

| ID | Category | Risk | PA Clause | Prob | P10 ($M) | P50 ($M) | P90 ($M) | PERT mean | EV ($M) | PSC retained | P3 GOA retained |
|----|----------|------|-----------|------|----------|----------|----------|-----------|---------|--------------|------------------|
| R01 | Construction | Cost overrun | Sch 14 §3.2(a) | 70% | 12.5 | 25.0 | 50.0 | 27.08 | 18.96 | 100% | 0% |
| R02 | Construction | Schedule delay | Sch 14 §3.2(b) | 40% | 6.0 | 12.0 | 24.0 | 13.00 | 5.20 | 100% | 0% |
| R03 | Operating | O&M cost variance | Sch 16 §4.1 | 60% | 4.8 | 8.0 | 14.0 | 8.47 | 5.08 | 100% | 0% |
| R04 | Operating | Lifecycle underestimation | Sch 16 §4.3 | 50% | 9.0 | 15.0 | 26.2 | 15.87 | 7.93 | 100% | 0% |
| R05 | Demand | Demand/usage | Sch 11 §2.4 | 30% | 2.0 | 5.0 | 12.5 | 5.75 | 1.73 | Shared | 50% |
| R06 | Regulatory | Compliance change | Sch 17 §1.2 | 20% | 1.0 | 4.0 | 12.0 | 4.83 | 0.97 | Shared | 50% |
| R07 | Force Majeure | FM events | Sch 18 | 5% | 2.0 | 20.0 | **100.0** | 30.33 | 1.52 | Shared | 50% |
| R08 | Design | Design deficiency | Sch 4 §5.1 | 35% | 3.0 | 6.0 | 12.0 | 6.50 | 2.28 | P3 | 0% (GOA) |
| R09 | Commissioning | Handover risk | Sch 12 §3.1 | 25% | 1.2 | 3.0 | 7.5 | 3.45 | 0.86 | P3 | 0% (GOA) |
| R10 | Technology | Obsolescence | Sch 16 §4.5 | 20% | 1.5 | 5.0 | 15.0 | 6.08 | 1.22 | P3 | 0% (GOA) |

### Risk summary

- **Total risk EV (all risks)**: $45.73M
- **PSC retained risk EV** (under DB comparator): $39.28M
- **P3 GOA retained risk EV**: $2.10M
- **Risk Transfer Value (PSC retained – P3 GOA retained)**: **$37.17M**

The Risk Transfer Value of $37.17M is a principal driver of the VfM recommendation.

## Residual value and refinancing

- Asset useful life: 40 years
- Land value: $25M
- Handback reserve: 5% of capital
- Handback condition discount: 15% (wear factor)
- Refinancing year: Year 3 (start of operations)
- Post-refi interest rate: 4.0%
- GOA gainshare: 50/50

## Model's own documented assumptions (Assumption_Log)

| ID | Assumption | Value | Source |
|----|-----------|-------|--------|
| A01 | Discount rate (real) | 6.0% | AB Treasury Board Directive 2019-04 |
| A07 | Debt interest rate | 5.5% | Market survey + 50 bps construction premium |
| A08 | Equity target return | 14% | Market comparables (Plenary, PCL, Graham) |
| A13 | P3 capital efficiency | –7% | P3 Canada benchmarking study 2022 |
| A14 | Cost overrun probability | 70% | Flyvbjerg reference class forecasting |
| A15 | Cost overrun P50 | $25M | AB historical data (5-yr avg) |
| A16 | Asset useful life | 40 yrs | Hospital asset class standard |
| A17 | Land value | $25M | Site appraisal (dated 2024-01) |

## The question

You are advising the Alberta Treasury Board, which meets to decide whether to proceed with the recommended P3 DBFM delivery or to choose conventional DB delivery. You have read the VfM analysis and this scenario brief. What is your analysis? What would you recommend, with what confidence, and why?
