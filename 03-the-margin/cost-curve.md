# BJJ Ready to Go — Cost Curve

## Product and Planning Assumptions

BJJ Ready to Go helps athletes prepare for competitions through
personalized preparation plans, weight tracking and readiness insights.

Planned integrations include Garmin, WHOOP and Apple Watch.

The figures below are planning assumptions for the course exercise.
Validate them through a pilot before committing to pricing.

| Assumption | Value | Basis |
|---|---:|---|
| Core subscription | $20/user/month | Selected price hypothesis |
| Daily summaries | 30/user/month | One summary per day |
| Weekly preparation reviews | 4/user/month | Approximately one per week |
| Video analysis adoption | 30% of subscribers/month | Demand hypothesis |
| Video analyses per buyer | 2/month | Frequency hypothesis |
| Video add-on price | $5/analysis | Proposed price |
| Maximum video length | 10 minutes | Defines the purchased unit |
| Small-model cost per summary | $0.001 | Illustrative estimate |
| Mid-model cost per review | $0.01 | Illustrative estimate |
| Direct cost per video analysis | $1.50 | Initial cost budget |

The video budget includes inference, media processing, direct
storage and direct human review averaged across analyses.

Model costs are illustrative estimates rather than quoted vendor
prices. Measure actual calls, tokens, retries and review time.

## Packaging Decision

| Role | Feature | Packaging |
|---|---|---|
| Leader | Personalized competition preparation plan with weight and readiness tracking | Included in the $20/month subscription |
| Filler | Daily summaries and weekly preparation reviews using training and wearable data | Included within the plan allowances |
| Killer | AI analysis of sparring videos with technical feedback | Paid add-on at $5 per video |

### Included Allowances

- Preparation dashboard and weight tracking.
- Wearable data synchronization.
- 30 daily summaries per billing month.
- 4 weekly preparation reviews per billing month.
- Video analysis purchased separately, up to 10 minutes per video.

### Rationale

Competition preparation is the main reason to subscribe, so the
preparation workflow belongs in the core product.

Video analysis serves a smaller segment and creates costs with each
upload. Per-video pricing connects revenue to usage and protects
the subscription from unrestricted video processing costs.

The assumed monthly video adoption is 30%. The course's 70% rule
supports testing an add-on, alongside willingness to pay, cost,
quality and the role of the feature in the product's core promise.

## Cost Model

### Core Subscription

Model tiers describe intended workloads. Select vendors and models
after evaluating representative BJJ cases.

| Feature | Complexity | Model tier | Cost per call | Calls/user/month | Share of core calls | Monthly cost |
|---|---|---|---:|---:|---:|---:|
| Daily readiness summary | Simple | Small | $0.001 | 30 | 88.24% | $0.03 |
| Weekly preparation review | Medium | Mid | $0.01 | 4 | 11.76% | $0.04 |
| Total | | | | 34 | 100% | $0.07 |

Calculations:

- Daily summaries = 30 × $0.001 = $0.03.
- Weekly reviews = 4 × $0.01 = $0.04.
- Monthly core model cost = $0.03 + $0.04 = $0.07.
- Blended core cost per call = $0.07 ÷ 34 = $0.00206.

The denominator is 34 because the plan assumes 30 summary calls
and 4 review calls before retries and escalations.

### Video Add-on

| Metric | Per analysis |
|---|---:|
| Revenue | $5.00 |
| Budgeted direct cost | $1.50 |
| Revenue after modeled direct cost | $3.50 |
| Margin after modeled direct cost | 70% |

One purchased analysis is a completed review of one video up to
10 minutes long. It may require multiple model calls.

### Blended Monthly Economics

Use a cohort of 100 paying subscribers:

- Subscription revenue = 100 × $20 = $2,000.
- Video buyers = 100 × 30% = 30.
- Video analyses = 30 × 2 = 60.
- Video revenue = 60 × $5 = $300.
- Core model cost = 100 × $0.07 = $7.
- Video direct cost = 60 × $1.50 = $90.

| Metric | Per 100 subscribers | Per subscriber |
|---|---:|---:|
| Subscription revenue | $2,000 | $20.00 |
| Video add-on revenue | $300 | $3.00 |
| Total revenue | $2,300 | $23.00 |
| Core model cost | $7 | $0.07 |
| Video direct cost | $90 | $0.90 |
| Total modeled direct cost | $97 | $0.97 |
| Revenue after modeled direct costs | $2,203 | $22.03 |
| Margin after modeled direct costs | 95.78% | 95.78% |

Expected video usage per subscriber is:

30% adoption × 2 analyses = 0.6 analyses/month.

### Margin Calculator

For this calculator, a request means one completed user task:
a daily summary, a weekly review or a video analysis.

This unit differs from an individual model call. A video analysis
may require several calls, all included in its direct-cost budget.

| Metric | Baseline | Stress — costs ×3 |
|---|---:|---:|
| Average completed tasks/user/month | 34.6 | 34.6 |
| Blended modeled cost per task | $0.02803 | $0.08410 |
| Monthly modeled COGS/user | $0.97 | $2.91 |
| Revenue/user/month | $23.00 | $23.00 |
| Revenue minus modeled COGS/user | $22.03 | $20.09 |
| Margin after modeled COGS | 95.78% | 87.35% |

Calculations:

- Tasks = 30 + 4 + (30% × 2) = 34.6.
- Monthly cost = (30 × $0.001) + (4 × $0.01)
  + (0.6 × $1.50) = $0.97.
- Blended cost per task = $0.97 ÷ 34.6 = $0.02803.
- Monthly revenue = $20 + (0.6 × $5) = $23.
- Baseline margin = ($23 − $0.97) ÷ $23 = 95.78%.
- Stress cost = $0.97 × 3 = $2.91.
- Stress margin = ($23 − $2.91) ÷ $23 = 87.35%.

Use unrounded values in calculations.

The $0.00206 core cost per call covers the text workload.
The $0.02803 blended cost per task also includes video processing.

## Cascading Strategy

### Initial Routing

| Task | Initial approach | Escalation |
|---|---|---|
| Weight trends, dates and dashboard calculations | Deterministic code | Flag missing or inconsistent data |
| Daily summary | Small model | Mid model if checks identify an unresolved issue |
| Weekly preparation review | Mid model | Stronger model or human review when necessary |
| Sparring video analysis | Media processing and a capable multimodal model | Human review when technical feedback cannot be supported |

Use the least expensive approach that meets quality and
response-time requirements.

### Routing and Quality Checks

- Validate input completeness.
- Check numerical outputs against deterministic calculations.
- Check whether conclusions are supported by the supplied data.
- Escalate unresolved cases.
- Record calls, retries and human review against the completed task.

The planned core mix is 88.24% small-model calls and 11.76%
mid-model calls before retries and escalations.

When a cascade calls two models, include both calls in its cost.
Measure the actual routing mix during the pilot.

### Evaluation

Build a reference set of representative cases with reviewed answers.
Compare models and routing rules using:

- Correctness and usefulness.
- Unsupported claims.
- Response time.
- Escalation and repeat-request rates.
- Total cost per correctly completed task.

## Pricing Model

### Proposed Structure

| Element | Proposed pricing |
|---|---|
| Core plan | $20 per athlete per month |
| Included AI usage | 30 daily summaries and 4 weekly reviews |
| Add-on unit | One completed video analysis, up to 10 minutes |
| Add-on price | $5 per analysis |
| Overall model | Subscription plus usage |
| Expected blended revenue | $23 per subscriber per month |

The initial strategy is to offer an accessible subscription and
charge separately for video analysis.

Validate willingness to pay and repeat usage before expanding
the included allowances.

### Value Validation

Test whether athletes:

- Understand and repeatedly use the preparation plan.
- Find the summaries useful.
- Purchase video analysis at $5.
- Return for another analysis.
- Continue subscribing between competitions.

## Stress Tests

### Direct Costs Increase

Hold prices, adoption and usage constant. Apply the multiplier to
all modeled direct costs as a conservative cost stress.

| Metric | Baseline | Costs +50% | Costs ×3 |
|---|---:|---:|---:|
| Core cost/user/month | $0.07 | $0.105 | $0.21 |
| Cost per video analysis | $1.50 | $2.25 | $4.50 |
| Blended direct cost/user/month | $0.97 | $1.455 | $2.91 |
| Blended revenue/user/month | $23.00 | $23.00 | $23.00 |
| Revenue after modeled direct costs | $22.03 | $21.545 | $20.09 |
| Margin after modeled direct costs | 95.78% | 93.67% | 87.35% |
| Video add-on margin | 70% | 55% | 10% |

The modeled portfolio remains above the course's 40% stress
threshold.

However, the video add-on falls to 10% margin when its direct
cost triples. Each analysis then contributes only $0.50 before
remaining delivery costs.

Monitor the add-on separately from the portfolio average.
At higher costs, review processing design, model selection,
video duration and pricing.

### Video Adoption Changes

Hold purchase frequency at 2 videos per buyer and direct cost
at $1.50 per analysis.

| Monthly adoption | Videos/subscriber | Revenue/subscriber | Modeled direct cost/subscriber | Revenue after modeled direct costs |
|---|---:|---:|---:|---:|
| 10% | 0.2 | $21.00 | $0.37 | $20.63 |
| 30% | 0.6 | $23.00 | $0.97 | $22.03 |
| 70% | 1.4 | $27.00 | $2.17 | $24.83 |

Higher adoption increases revenue because each analysis is
charged separately.

Reconsider bundling after measuring adoption, willingness to pay,
costs and effects on conversion and retention.

## Decision Criteria

### Core Subscription

Validate:

- Willingness to pay $20/month.
- Useful preparation outputs.
- Acceptable response time.
- Total delivery costs consistent with the target margin.

### Video Add-on

Initial pilot targets:

- At least 30% monthly adoption among paying subscribers.
- Average direct cost no higher than $1.50 per analysis.
- At least 80% of surveyed buyers rate the feedback as useful.
- Technical feedback passes expert review for supported claims.

These targets are hypotheses for the pilot.

## Cost Coverage and Limitations

The model currently includes:

- Core AI generation costs.
- A combined direct-cost budget for video analysis.

Add measured costs for:

- Core hosting, database and storage.
- Wearable integration operations and applicable fees.
- Payment processing.
- Customer support.
- Core retries, escalations and human review.
- Refunds and service credits.

When replacing the combined $1.50 video budget with measured
components, remove the combined budget to avoid double counting.

The reported percentages measure margin after modeled direct costs.
Complete gross margin requires all applicable cost of revenue.
Operating profit also requires operating expenses.

## Current Decision

Test the $20 core subscription and $5 video add-on.

The assumptions suggest sufficient room to investigate the product
economics further. The video add-on is the clearest cost sensitivity.

Confirm quality, willingness to pay and complete delivery costs
before treating the modeled margins as achievable.

## Next Actions

1. Measure calls, tokens and retries for daily and weekly outputs.
2. Benchmark video processing and expert-review costs.
3. Test subscription and add-on willingness to pay.
4. Evaluate candidate models and routing rules on reviewed cases.
5. Add the remaining delivery costs.
6. Replace assumptions with pilot results and recalculate.
