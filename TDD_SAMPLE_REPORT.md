# SAMPLE: investment committee technology diligence, Example Analytics Co.

> **Illustrative sample by Kunjar Bhaduri, Bhaduri Advisory. Fictional organization and invented evidence only. No client relationship or confidential engagement material. Prepared with AI drafting assistance under my direction. Revised October 2, 2026 (America/Chicago).**

## Investment question and recommendation

The fictional buyer plans to grow ARR from $8M to $16M in 24 months, with enterprise reporting and a scoring feature supporting expansion. The technology question is whether reporting remains dependable as usage and enterprise obligations grow, and whether the team can deliver that plan without depending on one engineer. These are scenario assumptions, not a forecast.

I would keep the transaction under review while resolving the reliability and recovery gaps below. The available evidence does not support an unconditional proceed recommendation or a conclusion about valuation. Before the committee commits, I would ask for a witnessed restore, incident reconciliation and a staffing commitment for the scoring pipeline. If those cannot be completed before signing, the deal team should assess conditions, remediation funding and the effect on its operating assumptions. Legal and commercial terms remain the deal team's decision.

| Area | Rating | Decision implication | Confidence |
|---|---|---|---|
| Architecture | Amber | Scoring, billing and authorization share a deployable monolith. Test failure isolation before enterprise expansion. | Medium |
| Delivery | Amber | API tests exist; scoring regression checks are absent in the inspected pipeline. | Medium |
| Reliability and recovery | Red | 11 labeled Sev-1 incidents in 90 days; recovery capability is unverified. | Medium |
| Security | Amber | Shared CI admin access creates accountability and access-control risk. | Medium |
| Data | Amber | Two inbound feeds have no documented schema or freshness contract. | Medium |
| Team continuity | Red | One engineer owns scoring code and production deployment. | Medium |
| Scale over 24 months | Amber | Low average database utilization does not establish end-to-end headroom. | Low |
| AI feature | Amber | Vendor-backed summaries lack recorded evaluation thresholds and per-tenant cost limits. | Medium |

Rating rule: Red materially threatens the investment thesis or continuity and needs a decision condition; Amber requires mitigation or further evidence; Green would require sufficient evidence against the agreed use case. Confidence reflects coverage, not likelihood of success.

## Evidence register (all fictional)

| ID | Artifact and coverage | Finding supported | Gap or conflict |
|---|---|---|---|
| E01 | 90-day incident export, 11 Sev-1 labels; seven linked to scoring failures | R1 | Reconcile severity definitions, account impact and support tickets; labels are management's classification |
| E02 | 20 sampled pipeline runs and CI configuration | R1, A1 | No completion/freshness alert in sampled configuration; full historical configurations not examined |
| E03 | 12-month commit history plus deployment access list | R2 | Other engineers' contribution through pairing may not appear in commit authorship |
| E04 | Current cloud settings and CI access listing | A1, R1 | MFA enabled on cloud console; three people use shared CI admin credential; restore success not demonstrated |
| E05 | Customer concentration export | R1 | Top ten accounts are 58% of fictional ARR; specific renewal exposure needs account-level validation |
| E06 | Seven days of average database utilization, about 15%; service map | A2 | No peak-query, queue, connection-pool or whole-system load test |
| E07 | Vendor contract, summary endpoint and sample application logs | A3 | Usage settings, data retention and customer obligations need cross-checking |
| E08 | Management growth plan and four interviews | All | Assertions remain interview evidence until reconciled with operating artifacts |
| E09 | Two feed adapters, sampled seven-day import logs and data-owner interview | A4 / Data Amber | No documented schema/freshness contracts supplied for either sampled feed; full historical validation logic and feed rights remain unverified. Medium confidence. |

## Findings tied to value and a next decision

**R1. Reporting reliability and recovery.** Seven E01 incidents were attributed to the nightly scoring job; customers noticed first in five. That raises renewal and support risk because reporting is central to the growth plan. E02 supports a missing freshness alert in the sample inspected. No successful restore record was supplied (E04), so recovery performance is unknown. Engineering should add completion, freshness and row-count alerts, then validate the scoring path and witness an isolated restore. Acceptance requires an alert deliberately triggered and acknowledged, passing regression fixtures, a recorded recovery time and a measured data loss window against business-approved RTO/RPO. The committee needs the account-level exposure, not an invented churn forecast.

**R2. Pipeline continuity.** E03 shows one principal author and one person able to deploy scoring. Losing that person could delay incident recovery and product work. The CTO should assign a second engineer, pair on failure diagnosis and move deployment to named CI permissions. Acceptance is a second engineer independently deploying, rolling back and recovering the pipeline using the runbook. The buyer should confirm staffing and consider retention with the deal team; commit count alone does not establish the full bus factor.

**A1. Shared privileged access.** E04 shows a shared CI admin credential, and the inspected repository has no dependency or secret-scanning gate. Rotate the shared credential, use named least-privilege identities, review existing exposure and add scanning with an owner for exceptions. Acceptance requires access evidence and a demonstrated revoked identity failing to deploy. Assess findings before making customer security commitments; a readiness plan is not an attestation report.

**A2. Capacity and cost.** E06 supports low average database utilization during seven days, but does not validate the intended load or enterprise latency targets. Benchmark critical journeys at current, 3x and the plan's peak usage, including scoring duration, vendor quotas, queue lag and p95 latency. Record cloud and vendor cost per report and active customer. Keep architecture changes conditional on the bottleneck found. There is no evidence here to justify either a rewrite or a fivefold scale claim.

**A3. AI and data obligations.** E07 does not demonstrate evaluation quality, per-tenant spend controls or alignment of vendor settings with customer contracts. Product and engineering should establish a representative, cleared evaluation set, log model/prompt versions, define failure handling and review data-use terms with counsel. Acceptance is a failed evaluation blocking a release, a spend limit exercised, and documented approval of the relevant data boundary.

**A4. Feed reliability (Data Amber).** E09 supports missing documented schema/freshness contracts for the two inspected feeds, not a conclusion that no validation exists anywhere. A silently malformed or stale feed could distort customer reports and scores. The data owner should define required fields, canonical dates/IDs, freshness thresholds, quarantine handling and an escalation owner for each feed. Acceptance requires an invalid-schema fixture quarantined without changing accepted scores, a stale-feed fixture alerting the named responder, and reconciliation of accepted/quarantined row counts. This is included in the AI/data-contract workstream below; confirm effort with the actual adapters.

## 100-day value creation plan and illustrative funding model

Engineering lead owns execution; CTO owns priorities; product owner accepts customer behavior; buyer operating partner reviews conditions. A five-day diligence window identifies risks; it does not complete this remediation.

| Workstream | Illustrative effort | Sequence | Acceptance evidence |
|---|---|---|---|
| Reliability, scoring regression checks and recovery | 250-400 hours | Days 1-30, then drills | Alert exercise, fixture results, RTO/RPO record |
| Knowledge transfer, deployment and rollback | 250-450 hours | Days 1-60 | Independent second-engineer deployment and recovery |
| Access cleanup and scanning | 150-250 hours | Immediate containment; days 1-30 | Named access, rotation, revoked-access and scan results |
| Capacity and unit-cost baselines | 150-250 hours | Days 15-60 | Reproducible load results and unit-cost baseline |
| AI evaluation and data-contract controls | 150-250 hours | Days 15-75 | Failed-evaluation gate, spend test and validated feeds |
| Handoff, evidence reconciliation and retesting | 50-100 hours | Through day 100 | Risk register, owners and rechecked acceptance |

Total: **1,000-1,700 hours**. At an illustrative blended delivery rate of **$125/hour**, labor is **$125,000-$212,500**. A 15% contingency gives **$143,750-$244,375**, rounded for planning to **$145K-$245K**. This is a worked scenario, not a quote. Efforts cover separate workstreams and must be estimated without double-counting in a real backlog. Cloud, vendors, audit fees, legal work and taxes are excluded. With approximately 14 weeks in a 100-calendar-day window, this effort needs roughly 71-121 team delivery hours a week. Confirm the actual holiday calendar and competing roadmap demand before adopting dates.

At day 30, reconsider the growth plan if recovery or staffing conditions fail. At day 60, use load and cost results to choose the capacity work. At day 100, review the residual risks with the board; a calendar milestone does not itself turn a Red Green.

## Method and limits

Assumed five business days, read-only source/cloud access, four interviews, the artifacts in E01-E09 and sampled production configuration. The committee receives the evidence register, material conflicts, conditions and plan. No penetration test, comprehensive license audit, independent financial audit or legal opinion is implied. No real artifacts were inspected for this fictional report. No adverse IP claim appears in the assumed materials; that is not proof of clean ownership. An actual deal needs contributor agreements, open-source and third-party licenses, data rights, customer obligations and any carve-out/shared-service dependence reviewed before closing. Unknowns remain visible until verified.
