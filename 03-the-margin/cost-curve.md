# BJJ Ready to Go — Cost Curve

## Product and Planning Assumptions

BJJ Ready to Go helps athletes prepare for competitions through
personalized plans, weight tracking and readiness insights.

Planned integrations include Garmin, WHOOP and Apple Watch.

All figures are planning assumptions for the course exercise.
Costs are illustrative budgets rather than vendor quotations.
Validate them through a paid pilot.

| Assumption | Value |
|---|---:|
| Core subscription | $20/user/month |
| Daily summaries | 30/user/month |
| Weekly preparation reviews | 4/user/month |
| Small-model call | $0.001 |
| Mid-model call | $0.01 |
| Additional Frontier call | $0.05 |
| Text tasks requiring Frontier escalation | 10% |
| Video adoption | 30% of subscribers/month |
| Videos per buyer | 2/month |
| Video price | $5/analysis |
| Maximum video length | 10 minutes |
| Direct cost per video analysis | $1.50 |

Video cost includes inference, media processing, direct storage
and direct human review averaged across analyses.

## Packaging Decision

| Role | Feature | Packaging |
|---|---|---|
| Leader | Competition preparation plan with weight and readiness tracking | Included in subscription |
| Filler | Daily summaries and weekly preparation reviews | Included within allowances |
| Killer | Sparring video analysis with technical feedback | Paid add-on |

### Plan Allowances

- Preparation dashboard and weight tracking.
- Wearable data synchronization.
- 30 daily summaries per billing month.
- 4 weekly preparation reviews per billing month.
- Video analysis purchased separately at $5 per video.

### Rationale

Preparation is the core reason to subscribe.

Video analysis serves a smaller segment and creates costs with
every upload. Charging per analysis connects revenue to usage.

The assumed 30% monthly adoption supports testing an add-on.
Confirm packaging using willingness to pay, quality, costs and
retention. The course's 70% rule is an initial heuristic.

## Cost Model

### Features and Model Tiers

| Feature | Complexity | Initial tier | Initial cost/task | Tasks/user/month | Share of tasks |
|---|---|---|---:|---:|---:|
| Daily summary | Simple | Small | $0.001 | 30 | 86.71% |
| Weekly review | Medium | Mid | $0.01 | 4 | 11.56% |
| Video analysis | Complex | Capable multimodal / Frontier | $1.50 direct-cost budget | 0.6 | 1.73% |
| Total | | | | 34.6 | 100% |

A task is one completed user output and may require multiple calls.

Expected videos per subscriber:

30% adoption × 2 videos = 0.6/month.

### Core Text Costs Including Escalations

Assume 10% of text tasks require one additional Frontier call.

| Feature | Initial cost/month | Escalation cost/month | Total cost/month |
|---|---:|---:|---:|
| Daily summaries | 30 × $0.001 = $0.03 | 30 × 10% × $0.05 = $0.15 | $0.18 |
| Weekly reviews | 4 × $0.01 = $0.04 | 4 × 10% × $0.05 = $0.02 | $0.06 |
| Total | $0.07 | $0.17 | $0.24 |

Expected core calls per subscriber:

- 30 Small calls.
- 4 Mid calls.
- 3.4 additional Frontier calls.
- Total = 37.4 calls for 34 completed text tasks.

Core cost per completed text task:

$0.24 ÷ 34 = $0.00706.

### Weighted Cost per Completed Task

| Feature | Cost/task including modeled escalations | Share of tasks | Weighted contribution |
|---|---:|---:|---:|
| Daily summary | $0.006 | 86.71% | $0.00520 |
| Weekly review | $0.015 | 11.56% | $0.00173 |
| Video analysis | $1.50 | 1.73% | $0.02601 |
| Blended | | 100% | $0.03295 |

Use unrounded values in calculations.

- Daily cost = $0.001 + (10% × $0.05) = $0.006.
- Weekly cost = $0.01 + (10% × $0.05) = $0.015.
- Monthly cost = $0.18 + $0.06 + (0.6 × $1.50) = $1.14.
- Blended cost = $1.14 ÷ 34.6 = $0.03295.

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
- Core model costs = 100 × $0.24 = $24.
- Video direct costs = 60 × $1.50 = $90.

| Metric | Per 100 subscribers | Per subscriber |
|---|---:|---:|
| Subscription revenue | $2,000 | $20.00 |
| Video revenue | $300 | $3.00 |
| Total revenue | $2,300 | $23.00 |
| Core model costs | $24 | $0.24 |
| Video direct costs | $90 | $0.90 |
| Total modeled direct costs | $114 | $1.14 |
| Revenue after modeled direct costs | $2,186 | $21.86 |
| Margin after modeled direct costs | 95.04% | 95.04% |

### Margin Calculator

Request means one completed user task in this table.

| Metric | Baseline | Stress — costs ×3 |
|---|---:|---:|
| Requests/user/month | 34.6 | 34.6 |
| Blended modeled cost/request | $0.03295 | $0.09884 |
| Monthly modeled COGS/user | $1.14 | $3.42 |
| Revenue/user/month | $23.00 | $23.00 |
| Revenue minus modeled COGS/user | $21.86 | $19.58 |
| Margin after modeled COGS | 95.04% | 85.13% |

Baseline margin = ($23 − $1.14) ÷ $23.

Stress margin = ($23 − $3.42) ÷ $23.

## Cascading Strategy

### Model Tiers

- Triage — Small.
- Standard preparation review — Mid.
- Escalation — Frontier.
- Video — capable multimodal / Frontier.

Select specific vendors and model versions through evaluation.

### Routing Rules

| Task | Initial approach | Escalation |
|---|---|---|
| Dates, weight trends and calculations | Deterministic code | Flag missing or inconsistent data |
| Daily summary | Small model | Frontier if checks identify an unresolved issue |
| Weekly review | Mid model | Frontier if checks identify an unresolved issue |
| Video analysis | Multimodal workflow | Human review when feedback cannot be supported |

Check numerical consistency, supporting evidence and defined
quality criteria. Request missing inputs when necessary.
Pass unresolved or approval-dependent cases to a qualified person.

### Expected Cascade Ratio

- 90% of text tasks complete without a Frontier call.
- 10% require one additional Frontier call.

The initial core call mix is 88.24% Small and 11.76% Mid.
This describes starting calls before escalation.

Charge both calls to the task when it escalates.

### Evaluation

Use representative cases with expert-reviewed answers.

Measure correctness, usefulness, unsupported claims, response time,
repeat requests, escalation failures and human review time.

Evaluate the routing rule and total cost per correctly completed
task alongside individual model performance.

## Pricing Model

### Strategy

Selected launch hypothesis — Penetrate.

Test a $20 monthly subscription among competition-focused athletes.
Sell costly video analysis separately.

Validate affordability, competitive positioning and willingness
to pay before confirming the strategy.

### Customer Value

- Preparation connected to a competition date.
- Weight and readiness information in one place.
- Less manual work combining training and wearable data.
- Technical feedback from purchased video reviews.

### Unit of Work

- Core billing unit — one athlete subscription month.
- Add-on unit — one completed video analysis up to 10 minutes.
- Completion means the analysis and feedback are delivered.
- Failed processing consumes no paid unit.
- Internal retries count toward delivery costs.

The purchased analysis does not guarantee a competition result.

### Price Structure

| Element | Proposed structure |
|---|---|
| Current pricing | Pre-launch, with no validated paid price |
| Core price | $20/athlete/month |
| Included AI allowance | 30 summaries and 4 weekly reviews |
| Add-on price | $5/completed video analysis |
| Pricing model | Hybrid subscription plus usage |
| Expected blended revenue | $23/subscriber/month |

Expected revenue:

$20 + (30% × 2 × $5) = $23/month.

### Value and Labor Test

Interview athletes and test paid purchases to establish:

- Time spent combining preparation data.
- Current alternatives and spending.
- Usefulness of video feedback for training decisions.
- Willingness to purchase again.

Measure claimed time savings before using them in marketing.

Track conversion, repeat purchases, retention, refunds and perceived
value alongside delivery costs.

## Stress Tests

### Direct Costs Increase

Hold revenue, usage and escalation rates constant.
Apply multipliers to all modeled direct costs.

| Metric | Baseline | Costs +50% | Costs ×3 |
|---|---:|---:|---:|
| Core cost/user/month | $0.24 | $0.36 | $0.72 |
| Cost/video | $1.50 | $2.25 | $4.50 |
| Blended cost/user/month | $1.14 | $1.71 | $3.42 |
| Revenue/user/month | $23.00 | $23.00 | $23.00 |
| Revenue after modeled costs | $21.86 | $21.29 | $19.58 |
| Margin after modeled costs | 95.04% | 92.57% | 85.13% |
| Video add-on margin | 70% | 55% | 10% |

The portfolio exceeds the course's 40% stress threshold under
these assumptions.

At triple cost, each $5 video leaves only $0.50 before remaining
delivery costs. Monitor video economics separately.

### Text Escalation Rate Changes

| Escalation rate | Core cost/user | Total modeled cost/user | Margin after modeled costs |
|---|---:|---:|---:|
| 0% | $0.07 | $0.97 | 95.78% |
| 10% | $0.24 | $1.14 | 95.04% |
| 30% | $0.58 | $1.48 | 93.57% |

Core cost = $0.07 + (34 × escalation rate × $0.05).

### Video Adoption Changes

Hold frequency at 2 videos per buyer and core cost at $0.24.

| Adoption | Videos/user | Revenue/user | Modeled cost/user | Revenue after modeled costs |
|---|---:|---:|---:|---:|
| 10% | 0.2 | $21.00 | $0.54 | $20.46 |
| 30% | 0.6 | $23.00 | $1.14 | $21.86 |
| 70% | 1.4 | $27.00 | $2.34 | $24.66 |

## Board One-Pager

### Decision Requested

Approve a pilot of the $20 core subscription with a $5 video
analysis add-on.

### Before and After

Both scenarios are hypothetical designs for a pre-launch product.

The comparison holds subscriber count and core service constant.
The "before" scenario is core-only. The "after" scenario adds paid
video analysis.

| Metric | Before — core only | After — core plus video |
|---|---:|---:|
| Monthly subscribers | 100 | 100 |
| Subscription price | $20 | $20 |
| Paid video analyses/month | 0 | 60 |
| Video price | — | $5 |
| Monthly revenue | $2,000 | $2,300 |
| Modeled direct costs | $24 | $114 |
| Revenue after modeled direct costs | $1,976 | $2,186 |
| Margin after modeled direct costs | 98.80% | 95.04% |

Before revenue = $20 × 100 = $2,000.

After revenue = ($20 × 100) + ($5 × 60) = $2,300.

After costs = $24 core costs + (60 × $1.50) = $114.

### Margin Shift

- Revenue increases by $300/month, or 15%.
- Modeled direct costs increase by $90/month.
- Revenue after modeled direct costs increases by $210/month.
- Per-subscriber contribution increases from $19.76 to $21.86.
- Margin decreases by 3.76 percentage points.
- Contribution dollars increase by 10.63%.

### Board Narrative

The video add-on lowers the blended margin percentage while adding
$210 in monthly contribution per 100 subscribers under the modeled
assumptions.

Each video contributes $3.50 after its modeled direct cost.
Per-analysis charging connects incremental revenue to usage.

Pilot approval depends on validating customer value, willingness
to pay, quality and complete delivery costs.

### Retention and NRR

Retention improvement is a hypothesis to test.

Measure NRR for the same customer cohort using starting revenue,
expansion, contraction and churn.

For illustration, a cohort starting at $2,000 and later generating
$2,300 would have 115% NRR if all revenue is comparable recurring
revenue and there is no contraction or churn.

Video purchases are usage-based and may be irregular. Report
subscription retention and repeat add-on revenue separately.

The 15% revenue uplift in this forecast is not an observed NRR result.

### Risks and Hedges

| Risk | Response |
|---|---|
| Video costs exceed the budget | Measure full cost, limit duration and revisit pricing |
| Feedback quality is weak | Expert evaluation and human handoff |
| Video buyers do not repeat | Test usefulness and repeat purchase |
| Athletes cancel between events | Measure retention across competition cycles |
| Portfolio averages hide weak video economics | Track core and add-on contribution separately |

## Pilot Decision Criteria

- Test willingness to pay $20/month.
- Target 30% monthly video adoption.
- Target video direct costs of $1.50 or less.
- Target at least 80% of surveyed buyers rating feedback useful.
- Require expert review of technical-feedback quality.
- Measure retention, repeat requests and human intervention.

These are initial planning targets.

## Cost Coverage and Limitations

Included:

- Initial core model calls.
- One Frontier call for 10% of text tasks.
- Combined direct-cost budget for video analysis.

Add measured costs for:

- Core hosting, database and storage.
- Wearable integrations and applicable fees.
- Payment processing.
- Customer support.
- Additional routing calls and retries.
- Human review outside the video budget.
- Refunds and service credits.

Replace the combined video budget with measured components,
avoiding double counting.

Reported margins cover modeled direct costs.
Complete gross margin requires all applicable cost of revenue.
Operating profit also requires operating expenses.

## Next Actions

1. Benchmark candidate models on reviewed BJJ cases.
2. Measure cost per correctly completed task.
3. Test escalation rules and human handoffs.
4. Measure video processing and review costs.
5. Validate pricing, repeat purchase and retention.
6. Add remaining costs and update the board comparison.
