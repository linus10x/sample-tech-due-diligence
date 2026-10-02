# SAMPLE technical due diligence report: "Example Analytics Co." (fictional)

> **Sample / illustrative. Example Analytics Co. does not exist. Every finding, number and name below is invented to show the format and the reasoning. This is not based on any real company, client, engagement or confidential material.** Prepared by Kunjar Bhaduri, Bhaduri Advisory, October 2, 2026, with AI drafting assistance under my direction.

**Engagement type (fictional):** buy-side technology diligence for a growth-equity investor. **Window:** 5 business days. **Access assumed:** read-only source repositories, cloud console, CI history, incident log, 4 management interviews.

---

## 1. Summary for the investment committee
| Area | Rating | One line |
|---|---|---|
| Product architecture | Amber | Sound core; one monolith service owns scoring, billing and auth |
| Code quality and delivery | Amber | Tests cover the API layer; the scoring pipeline has none |
| Reliability and operations | **Red** | 11 Sev-1 incidents in 90 days; no alerting on the scoring job; restores never tested |
| Security | Amber | MFA on cloud console; shared admin credentials in CI; no dependency scanning |
| Data | Amber | Customer data in one region; no data contract on inbound feeds |
| Team and key-person risk | **Red** | One engineer wrote and deploys the scoring pipeline |
| Scalability (next 24 months) | Green | Current load is under 15% of database capacity |
| AI components | Amber | LLM feature calls a vendor API with no evaluation set and no spend cap |

**Bottom line (fictional):** no finding blocks the deal. Two Reds are fixable in 90 days for an estimated $150K to $250K of engineering time, which should be reflected in the 100-day plan rather than the price. The investor should make a tested restore and a second engineer on the scoring pipeline conditions of the first board meeting.

## 2. Findings that matter to value
**R1. Reliability (Red).** Incident log shows 11 Sev-1s in 90 days, 7 traced to the nightly scoring job failing silently. Customers noticed first in 5 of them. *Evidence:* incident log export, CI history, interview with the head of engineering. *Impact:* churn risk in the top 10 accounts, which are 58% of ARR (fictional). *Fix:* alerting on job completion and row counts (1 week); a validation harness around the scoring job (2 to 3 weeks); a restore drill (1 day, then quarterly).

**R2. Key-person risk (Red).** One engineer is the only committer on the scoring pipeline in the last 12 months and holds the deploy credentials. *Fix:* pair a second engineer for 6 weeks, move deploys into CI with named approvers, document the pipeline. *Deal note:* consider a retention arrangement for this engineer.

**A1. Security (Amber).** A shared admin credential is stored as a CI variable and used by three people. No dependency or secret scanning. *Fix:* per-person access through SSO, rotate the credential, turn on scanning (2 weeks). *Note:* if enterprise customers expect a SOC 2 report, plan on a 9 to 12 month track to Type II; do not represent readiness before then.

**A2. AI feature (Amber).** The summary feature sends customer text to a model vendor with no evaluation set, no spend cap and no record of which prompts and versions produced which outputs. *Fix:* a fixed evaluation set with pass thresholds, a spend cap per tenant, and logging of model and prompt versions (2 to 3 weeks). Confirm the vendor's data-use terms against customer contracts.

## 3. What we did not find (equally useful to the investor)
- No sign of licensing problems in the dependency tree (sampled, not exhaustive).
- Cloud spend is in line with usage; no idle large resources.
- The architecture does not need a rewrite to reach 5x current load.

## 4. 100-day plan (fictional)
| Days | Outcome | Owner |
|---|---|---|
| 1 to 15 | Alerting on the scoring job; restore drill done and timed; shared credential rotated | Head of engineering |
| 16 to 45 | Validation harness in CI; second engineer pairing; dependency and secret scanning on | Head of engineering + 1 |
| 46 to 100 | AI evaluation set and spend caps; SOC 2 gap assessment if enterprise pipeline needs it; incident review cadence | CTO / fractional CTO |

## 5. Method and limits
- Read-only access, 5 days, 4 interviews. Code was sampled, not reviewed line by line.
- Ratings are judgments against the stated investment thesis, not a certification or an audit opinion.
- Cost estimates are ranges for planning, not quotes.
- No penetration test was performed.
