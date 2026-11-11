# BJJ Ready to Go — Cost Curve

## Product and Assumptions

BJJ Ready to Go helps athletes prepare for competitions through
personalized preparation plans, weight tracking and readiness insights.

Planned integrations include Garmin, WHOOP and Apple Watch.

All figures are planning assumptions for the course exercise.
Model costs are illustrative estimates rather than vendor quotations.

| Assumption | Value |
|---|---:|
| Core subscription | $20/user/month |
| Daily summaries | 30/user/month |
| Weekly preparation reviews | 4/user/month |
| Small-model call | $0.001 |
| Mid-model call | $0.01 |
| Additional Frontier call | $0.05 |
| Text tasks requiring Frontier escalation | 10% |
| Video analysis adoption | 30% of subscribers/month |
| Video analyses per buyer | 2/month |
| Video price | $5/analysis |
| Maximum video length | 10 minutes |
| Direct cost per video analysis | $1.50 |

Video cost includes inference, media processing, direct storage
and direct human review averaged across analyses.

## Packaging Decision

| Role | Feature | Packaging |
|---|---|---|
| Leader | Personalized competition preparation plan with weight and readiness tracking | Included in the subscription |
| Filler | Daily summaries and weekly preparation reviews | Included within plan allowances |
| Killer | AI analysis of sparring videos with technical feedback | Paid add-on |

### Plan Allowances

- Preparation dashboard and weight tracking.
- Wearable data synchronization.
- 30 daily summaries per billing month.
- 4 weekly preparation reviews per billing month.
- Video analysis purchased separately at $5 per video.

### Rationale

Competition preparation is the core reason to subscribe.

Video analysis serves a smaller segment and creates costs with
every upload. Per-video pricing connects revenue to usage.

Assumed video adoption is 30% monthly. Validate packaging using
adoption, willingness to pay, cost, quality and retention.
The course's 70% rule is an initial heuristic.

## Cost Model

### Features and Model Tiers

| Feature | Complexity | Initial tier | Initial cost/task | Tasks/user/month | Share of tasks |
|---|---|---|---:|---:|---:|
| Daily readiness summary | Simple | Small | $0.001 | 30 | 86.71% |
| Weekly preparation review | Medium | Mid | $0.01 | 4 | 11.56% |
| Sparring video analysis | Complex | Capable multimodal / Frontier | $1.50 direct-cost budget | 0.6 | 1.73% |
| Total | | | | 34.6 | 100% |

A task is one completed user output. A task can require multiple
model calls. Video cost covers the complete processing workflow.

The 0.6 expected videos per subscriber comes from:

30% adoption × 2 videos per buyer = 0.6.

### Core Text Costs Including Escalations

Assume 10% of daily summaries and weekly reviews require one
additional Frontier call.

| Feature | Initial monthly cost | Frontier escalation cost | Total monthly cost |
|---|---:|---:|---:|
| Daily summaries | 30 × $0.001 = $0.03 | 30 × 10% × $0.05 = $0.15 | $0.18 |
| Weekly reviews | 4 × $0.01 = $0.04 | 4 × 10% × $0.05 = $0.02 | $0.06 |
| Total | $0.07 | $0.17 | $0.24 |

Expected core calls per subscriber:

- 30 Small calls.
- 4 Mid calls.
- 3.4 additional Frontier calls.
- Total = 37.4 model calls for 34 completed tasks.

Average core cost per completed task:

$0.24 ÷ 34 = $0.00706.

### Weighted Cost per Completed Task

| Feature | Cost/task including modeled escalations | Share of tasks | Weighted contribution |
|---|---:|---:|---:|
| Daily summary | $0.006 | 86.71% | $0.00520 |
| Weekly review | $0.015 | 11.56% | $0.00173 |
| Video analysis | $1.50 | 1.73% | $0.02601 |
| Blended | | 100% | $0.03295 |

Calculations use unrounded task shares.

- Daily cost/task = $0.001 + (10% × $0.05) = $0.006.
- Weekly cost/task = $0.01 + (10% × $0.05) = $0.015.
- Monthly cost = 34.6 tasks × unrounded blended cost = $1.14.

The blended figure combines text generation costs and the broader
video direct-cost budget.

### Video Add-on Economics

| Metric | Per analysis |
|---|---:|
| Revenue | $5.00 |
| Modeled direct cost | $1.50 |
| Revenue after modeled direct cost | $3.50 |
| Margin after modeled direct cost | 70% |

### Blended Monthly Economics

For 100 paying subscribers:

- Subscription revenue = 100 × $20 = $2,000.
- Video buyers = 100 × 30% = 30.
- Video analyses = 30 × 2 = 60.
- Video revenue = 60 × $5 = $300.
- Core model costs including escalations = 100 × $0.24 = $24.
- Video direct costs = 60 × $1.50 = $90.

| Metric | Per 100 subscribers | Per subscriber |
|---|---:|---:|
| Subscription revenue | $2,000 | $20.00 |
| Video revenue | $300 | $3.00 |
| Total revenue | $2,300 | $23.00 |
| Core model costs including escalations | $24 | $0.24 |
| Video direct costs | $90 | $0.90 |
| Total modeled direct costs | $114 | $1.14 |
| Revenue after modeled direct costs | $2,186 | $21.86 |
| Margin after modeled direct costs | 95.04% | 95.04% |

### Margin Calculator

Request means one completed user task in this table.

| Metric | Baseline | Stress — costs ×3 |
|---|---:|---:|
| Average requests/user/month | 34.6 | 34.6 |
| Blended modeled cost/request | $0.03295 | $0.09884 |
| Monthly modeled COGS/user | $1.14 | $3.42 |
| Revenue/user/month | $23.00 | $23.00 |
| Revenue minus modeled COGS/user | $21.86 | $19.58 |
| Margin after modeled COGS | 95.04% | 85.13% |

- Revenue = $20 + (0.6 × $5) = $23.
- Cost = $0.24 + (0.6 × $1.50) = $1.14.
- Baseline margin = ($23 − $1.14) ÷ $23 = 95.04%.
- Stress margin = ($23 − $3.42) ÷ $23 = 85.13%.

## Cascading Strategy

### Models and Routing

- Triage model tier — Small.
- Standard review model tier — Mid.
- Escalation model tier — Frontier.
- Video model tier — capable multimodal / Frontier.
- Specific vendors and model versions — select through evaluation.

| Task | Initial approach | Escalation |
|---|---|---|
| Dates, weight trends and dashboard calculations | Deterministic code | Flag incomplete or inconsistent data |
| Daily summary | Small model | Frontier when validation identifies an unresolved issue |
| Weekly preparation review | Mid model | Frontier when validation identifies an unresolved issue |
| Video analysis | Multimodal processing workflow | Human review when feedback cannot be supported |

### Escalation Rules

Escalate when checks identify:

- Conflicting inputs that the initial output does not resolve.
- Numerical inconsistencies.
- Conclusions unsupported by the supplied evidence.
- Failure against the task's defined quality criteria.

Request missing information when necessary.
Pass unresolved or approval-dependent cases to a qualified person.

### Expected Cascade Ratio

- 90% of core text tasks complete without a Frontier call.
- 10% require one additional Frontier call.

This is a task escalation assumption.

The initial core call mix is 88.24% Small and 11.76% Mid.
That mix describes the planned starting calls.

Both calls are charged when a task escalates.
The cost model includes the expected additional Frontier calls.

### Evaluation

Use representative cases with expert-reviewed answers.

Compare:

- Correctness and usefulness.
- Unsupported claims.
- Response time.
- Escalation failures.
- Repeat requests.
- Human review time.
- Total cost per correctly completed task.

Test the escalation rule as well as individual models.

## Pricing Model

| Element | Proposed structure |
|---|---|
| Core price | $20/athlete/month |
| Included AI allowance | 30 daily summaries and 4 weekly reviews |
| Add-on unit | One completed video analysis up to 10 minutes |
| Add-on price | $5 |
| Pricing model | Subscription plus usage |
| Expected blended revenue | $23/subscriber/month |

Validate willingness to pay, repeat purchase and retention before
expanding the included allowances.

## Stress Tests

### Direct Costs Increase

Hold revenue, usage and escalation rates constant.
Apply each multiplier to all modeled direct costs.

| Metric | Baseline | Costs +50% | Costs ×3 |
|---|---:|---:|---:|
| Core cost/user/month | $0.24 | $0.36 | $0.72 |
| Cost/video analysis | $1.50 | $2.25 | $4.50 |
| Blended cost/user/month | $1.14 | $1.71 | $3.42 |
| Revenue/user/month | $23.00 | $23.00 | $23.00 |
| Revenue after modeled costs | $21.86 | $21.29 | $19.58 |
| Margin after modeled costs | 95.04% | 92.57% | 85.13% |
| Video add-on margin | 70% | 55% | 10% |

The portfolio exceeds the course's 40% stress threshold under
these assumptions.

Video analysis requires separate monitoring. At triple cost,
a $5 analysis leaves $0.50 before remaining delivery costs.

### Frontier Escalation Rate Changes

Hold other assumptions constant.

| Text escalation rate | Core cost/user | Total modeled cost/user | Margin after modeled costs |
|---|---:|---:|---:|
| 0% | $0.07 | $0.97 | 95.78% |
| 10% | $0.24 | $1.14 | 95.04% |
| 30% | $0.58 | $1.48 | 93.57% |

Core cost = $0.07 + (34 × escalation rate × $0.05).

Increase escalation when it improves successful resolution enough
to justify the added cost and response time.

### Video Adoption Changes

Hold frequency at 2 videos per buyer and core cost at $0.24.

| Monthly adoption | Videos/subscriber | Revenue/subscriber | Modeled cost/subscriber | Revenue after modeled costs |
|---|---:|---:|---:|---:|
| 10% | 0.2 | $21.00 | $0.54 | $20.46 |
| 30% | 0.6 | $23.00 | $1.14 | $21.86 |
| 70% | 1.4 | $27.00 | $2.34 | $24.66 |

## Pilot Decision Criteria

- Test willingness to pay $20/month for the core product.
- Target 30% monthly video adoption among paying subscribers.
- Target video direct costs of $1.50 or less per analysis.
- Target at least 80% of surveyed video buyers rating feedback useful.
- Require expert review of technical-feedback quality.
- Measure retention, repeat requests and human intervention.

These are initial planning targets.

## Cost Coverage and Limitations

Included:

- Initial core model calls.
- One Frontier call for 10% of core text tasks.
- Combined direct-cost budget for video analysis.

Add measured costs for:

- Core hosting, database and storage.
- Wearable integrations and applicable fees.
- Payment processing.
- Customer support.
- Additional retries and routing calls.
- Human review outside the video budget.
- Refunds and service credits.

Replace the combined video budget with measured components when
available, avoiding double counting.

Reported margins cover the modeled direct costs.
Complete gross margin requires all applicable cost of revenue.
Operating profit also requires operating expenses.

## Current Decision and Next Actions

Test the $20 subscription and $5 video add-on.

1. Benchmark candidate models on reviewed BJJ cases.
2. Measure real token usage and cost per completed task.
3. Test escalation rules and human handoffs.
4. Measure video processing and review costs.
5. Validate willingness to pay and repeat usage.
6. Add remaining delivery costs and recalculate margins.
