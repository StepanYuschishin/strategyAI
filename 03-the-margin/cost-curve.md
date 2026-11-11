# BJJ Ready to Go — Cost Curve

## Product and Assumptions

BJJ Ready to Go helps athletes prepare for competitions through
personalized preparation plans, weight tracking and readiness insights.

Supported wearable integrations are planned for Garmin, WHOOP and
Apple Watch.

All figures below are planning assumptions for the course exercise.
Replace them with pilot measurements before making launch decisions.

| Assumption | Value | Basis |
|---|---:|---|
| Core subscription | $20/user/month | Selected price hypothesis |
| Daily summaries | 30/user/month | One summary per day |
| Weekly preparation reviews | 4/user/month | Approximately one review per week |
| Video analysis adoption | 30% of subscribers/month | Initial demand hypothesis |
| Video analyses per buyer | 2/month | Initial frequency hypothesis |
| Video add-on price | $5/analysis | Proposed price |
| Maximum video length | 10 minutes | Defines the priced unit |
| Small-model cost per summary | $0.001 | Illustrative cost estimate |
| Mid-model cost per review | $0.01 | Illustrative cost estimate |
| Direct cost per video analysis | $1.50 | Initial cost budget |

The $1.50 video budget includes model inference, media processing,
direct storage and any direct human review averaged across analyses.
Its component costs must be measured during the pilot.

## Packaging Decision

| Role | Feature | Packaging |
|---|---|---|
| Leader | Personalized competition preparation plan with weight and readiness tracking | Included in the $20/month subscription |
| Filler | Daily readiness summaries and weekly preparation reviews using training and wearable data | Included within the allowances below |
| Killer | AI analysis of sparring videos with technical feedback | $5 per video of up to 10 minutes |

### Included Allowances

- 30 daily summaries per billing month.
- 4 weekly preparation reviews per billing month.
- Preparation dashboard and weight tracking.
- Wearable data synchronization.
- Video analysis purchased separately.

### Rationale

Competition preparation is the main reason to subscribe, so the
preparation workflow belongs in the core product.

Video analysis serves a smaller segment and creates costs with each
upload. Per-video pricing connects revenue to usage and limits the
risk of heavy users consuming the core subscription margin.

The assumed 30% monthly adoption supports testing video analysis
as an add-on. The course's 70% rule is a packaging heuristic.
Final packaging also depends on willingness to pay, costs and quality.

## Cost Model

### Core Subscription

Model tiers describe intended workloads. Vendor and model selection
will follow evaluations on representative BJJ cases.

| Feature | Complexity | Model tier | Cost per call | Calls/user/month | Share of core calls | Monthly cost |
|---|---|---|---:|---:|---:|---:|
| Daily readiness summary | Simple | Small | $0.001 | 30 | 88.24% | $0.03 |
| Weekly preparation review | Medium | Mid | $0.01 | 4 | 11.76% | $0.04 |
| Total | | | | 34 | 100% | $0.07 |

Calculations:

- Daily summaries = 30 × $0.001 = $0.03/month.
- Weekly reviews = 4 × $0.01 = $0.04/month.
- Core model cost = $0.03 + $0.04 = $0.07/user/month.
- Blended core cost per call = $0.07 ÷ 34 = $0.00206.

The denominator is 34 because the core plan assumes 30 daily
summary calls and 4 weekly review calls.

### Video Add-on

| Item | Amount |
|---|---:|
| Revenue per analysis | $5.00 |
| Budgeted direct cost per analysis | $1.50 |
| Contribution per analysis | $3.50 |
| Margin after modeled direct costs | 70% |

One purchased analysis is a completed review of one video up to
10 minutes long. It may require several model and processing calls.

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

Expected video usage is 0.6 analyses per subscriber per month:

30% adoption × 2 analyses = 0.6.

A video analysis can contain multiple calls, so it is excluded
from the blended core cost-per-call calculation.

## Cascading Strategy

### Initial Routing

| Task | Initial approach | Escalation |
|---|---|---|
| Weight trends, dates and dashboard calculations | Deterministic code | Flag missing or inconsistent data |
| Daily summary | Small model | Mid model if checks identify an unresolved issue |
| Weekly preparation review | Mid model | Stronger model or human review when necessary |
| Sparring video analysis | Media processing and a capable multimodal model | Human review when technical feedback cannot be supported |

Use the least expensive approach that meets the quality and
response-time requirements for each task.

### Router and Quality Checks

- Validate input completeness before generating advice.
- Check numerical outputs against deterministic calculations.
- Check whether conclusions are supported by the supplied data.
- Escalate unresolved cases rather than presenting unsupported certainty.
- Record every call, retry and human review against the completed task.

The initial 88.24% small / 11.76% mid mix describes planned core
calls before retries and escalations. It must be updated from logs.

### Evaluation

Build a reference set of representative cases with reviewed answers.
Compare candidate models and routing rules using:

- Correctness and usefulness.
- Unsupported claims.
- Response time.
- Escalation and repeat-request rates.
- Total cost per correctly completed task.

When a cascade calls two models, include both calls in the cost.

## Pricing Model

### Strategy

Start with an accessible subscription and charge separately for
video analysis. Test willingness to pay and repeat usage before
expanding the included allowances.

| Pricing element | Proposed structure |
|---|---|
| Core plan | $20 per athlete per month |
| Included AI usage | 30 daily summaries and 4 weekly reviews |
| Add-on unit | One completed video analysis, up to 10 minutes |
| Add-on price | $5 per analysis |
| Overall model | Subscription plus usage |
| Expected blended revenue | $23 per subscriber per month |

Current paid pricing has not been validated. These are proposed
prices for the exercise.

### Value Validation

Test whether athletes:

- Understand the preparation plan and use it repeatedly.
- Find the summaries helpful for preparation decisions.
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

The portfolio average can hide a weak add-on. At triple direct
cost, each $5 video analysis contributes only $0.50 before
remaining delivery costs.

### Video Adoption Changes

Hold purchase frequency at 2 videos per buyer and direct cost
at $1.50 per analysis.

| Monthly adoption | Videos/subscriber | Revenue/subscriber | Modeled direct cost/subscriber | Revenue after modeled direct costs |
|---|---:|---:|---:|---:|
| 10% | 0.2 | $21.00 | $0.37 | $20.63 |
| 30% | 0.6 | $23.00 | $0.97 | $22.03 |
| 70% | 1.4 | $27.00 | $2.17 | $24.83 |

Higher adoption increases revenue because each analysis is charged
separately. Reconsider bundling after measuring adoption, willingness
to pay and the effect on subscription conversion and retention.

## Decision Criteria

### Core Subscription

Proceed with the proposed structure if pilot data supports:

- Willingness to pay $20/month.
- Useful preparation outputs.
- Acceptable response time.
- Delivery costs consistent with the target margin.

### Video Add-on

Initial pilot targets:

- At least 30% monthly adoption among paying subscribers.
- Average direct cost no higher than $1.50 per analysis.
- At least 80% of surveyed buyers rate the feedback as useful.
- Technical feedback passes expert review for supported claims.

If costs exceed the budget, review model selection, video length,
processing design and pricing. Re-evaluate customer value before
reducing output quality.

## Cost Coverage and Limitations

The model currently includes:

- Core AI generation costs.
- A combined direct-cost budget for video analysis.

Add measured costs for:

- Core hosting, database and storage.
- Wearable integration operations and fees where applicable.
- Payment processing.
- Customer support.
- Core retries, escalations and human review.
- Refunds and service credits.

Avoid counting video costs twice when replacing its combined
$1.50 budget with measured component costs.

The reported percentages are margins after the modeled direct
costs. Full gross margin requires all applicable cost of revenue.
Operating profit also requires operating expenses.

## Next Actions

1. Measure tokens, calls and retries for daily and weekly outputs.
2. Benchmark video processing and expert-review costs.
3. Test the $20 subscription and $5 video price with athletes.
4. Run the reference cases through candidate routing setups.
5. Replace the assumptions with pilot results and recalculate.
