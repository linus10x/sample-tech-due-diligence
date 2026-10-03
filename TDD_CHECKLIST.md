# SAMPLE technical due diligence checklist (reusable)

> Sample / illustrative. A working checklist, not a client deliverable. Prepared by Kunjar Bhaduri, Bhaduri Advisory, with AI drafting assistance under my direction.

## Before access (day 0)
- [ ] Investment thesis in one paragraph: what must the technology do for the plan to work?
- [ ] Data room request sent: architecture diagram, repo list, cloud bill (12 months), incident log (12 months), org chart, vendor list and contracts, security policies, pen-test reports, customer security questionnaires answered in the last year
- [ ] Interviews booked: CTO or head of engineering, product lead, one senior engineer, whoever is on call

## Architecture and scalability
- [ ] Map of services, data stores and third parties; which ones are single points of failure
- [ ] Load today vs capacity; what breaks first at 3x and 10x
- [ ] Build-vs-buy decisions that look expensive to unwind

## Code and delivery
- [ ] Test coverage where it matters (money, scoring, auth), not overall percentage
- [ ] CI history: build frequency, failure rate, time to restore a broken main branch
- [ ] Deploy path: who can deploy, how, with what approvals; rollback tested?
- [ ] Bus factor per critical component (committers in last 12 months)

## Reliability and operations
- [ ] Incidents in last 90 days by severity and root cause; who noticed first, the customer or the team
- [ ] Monitoring and alerting on the jobs customers depend on
- [ ] Backups: what, how often, where; **when was a restore last actually tested, and how long did it take?**

## Security
- [ ] Identity: SSO, MFA, shared accounts, offboarding
- [ ] Secrets: where they live; scanning on?
- [ ] Dependency scanning and patch cadence
- [ ] Customer commitments already made (security questionnaires, contract clauses) vs reality
- [ ] SOC 2: report availability, Type I or Type II, CPA firm, system scope and report date/period; distinguish readiness from an issued report
- [ ] ISO/IEC 27001: readiness or certification status, standard edition, certified scope, issuing certification body and certificate validity; inspect the actual certificate

## Data
- [ ] Data contracts on inbound feeds; data quality incidents
- [ ] Residency, retention and deletion vs customer contracts and privacy law
- [ ] Ownership and licence of any third-party data

## AI components
- [ ] Which features use models; which vendors; data-use terms
- [ ] Evaluation set and pass thresholds; regression checks on model or prompt changes
- [ ] Spend caps, rate limits, fallbacks; logging of model and prompt versions
- [ ] Any autonomous action (writes, emails, payments) and the human approval around it

## Team
- [ ] Org, tenure, attrition, open roles; contractor dependence
- [ ] Engineering cost per unit of output trend
- [ ] Leadership gaps the plan will expose

## Report
- [ ] One-page summary with Red / Amber / Green and a bottom line
- [ ] Findings tied to evidence and to value (revenue, cost, risk)
- [ ] Unknowns, conflicts, confidence and negative findings bounded by inspected evidence
- [ ] 100-day plan with owners and cost ranges
- [ ] Method and limits stated plainly

## Deal structure, ownership and value creation
- [ ] Investment thesis assumptions translated into required capacity, reliability, costs and enterprise obligations
- [ ] Software and data rights: contributor agreements, acquired IP, open-source obligations and vendor restrictions; counsel validates legal conclusions
- [ ] Carve-out or acquisition integration: shared infrastructure, identity, contracts, people, transitional services, dependencies and exit costs
- [ ] Cloud/vendor unit costs and customer margin implications; reconcile management projections with observed workloads
- [ ] Each material finding has an evidence ID, coverage, confidence, commercial consequence, accountable owner, acceptance test and decision condition
- [ ] Estimated hours, delivery capacity, rate, contingency and exclusions support cost/date ranges; no unsupported valuation recommendation
