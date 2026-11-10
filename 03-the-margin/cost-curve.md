# Cost Curve — BJJ Ready to Go

## Assumptions

All figures are planning hypotheses, not validated results.

- Base subscription: $20 per athlete/month.
- Deep preparation review add-on: $5 per completed review.
- Base monthly usage: 30 daily summaries and 4 weekly analyses.
- Deep-review adoption: 30% of subscribers buy one review/month.
- AI request costs: Small $0.001, Mid $0.010, Frontier $0.050.
- Specific providers and models: Not yet selected.
- Potential wearable sources: Garmin, WHOOP, and Apple Watch.
- Data imports and basic calculations use regular software, not LLM calls.
- Wearable integration availability and costs require verification.

## Packaging Decision

| Category | Feature | Rationale |
|---|---|---|
| Leader | Competition readiness dashboard combining weight, training, recovery, and competition date | Main reason athletes would subscribe |
| Filler | Daily AI summaries and weekly trend explanations | Adds convenience and context |
| Killer | On-demand deep competition preparation review | Potentially expensive, occasional feature that may justify separate pricing |

### Killer Usage

- Actual adoption: Unknown.
- Planning assumption: 30% of monthly subscribers.
- This measures the percentage of users buying a review, not the percentage of AI requests.
- Course heuristic: Below 70% adoption, consider an add-on.
- Initial decision: Bundle routine preparation; sell deep reviews separately.
- Reconsider after measuring demand, cost, and willingness to pay.

## Cost Model

### Per-Feature Estimates

| Feature | Complexity | Model tier | Cost/request | Requests per adopting user/month |
|---|---|---|---:|---:|
| Daily summary | Simple | Small | $0.001 | 30 |
| Weekly analysis | Medium | Mid | $0.010 | 4 |
| Deep preparation review | Complex | Frontier | $0.050 | 1 |

Costs are illustrative assumptions, not verified provider prices.

### Base Subscription

Monthly requests:
30 + 4 = 34.

Monthly AI cost:
(30 × $0.001) + (4 × $0.010) = $0.07.

Blended cost per request:
$0.07 ÷ 34 ≈ $0.00206.

| Tier | Requests/month | Volume share | Weighted cost/request |
|---|---:|---:|---:|
| Small | 30 | 88.24% | $0.00088 |
| Mid | 4 | 11.76% | $0.00118 |
| Blended | 34 | 100% | $0.00206 |

Weighted cost/request = tier cost/request × its request share.

### Add-On and Portfolio Average

Assuming 30% of subscribers buy one deep review/month:

- AI cost per deep review: $0.05.
- Average additional requests/subscriber: 30% × 1 = 0.3.
- Average add-on AI cost/subscriber: 30% × $0.05 = $0.015.
- Average total requests/subscriber: 34 + 0.3 = 34.3.
- Average total AI cost/subscriber: $0.07 + $0.015 = $0.085.
- Portfolio blended cost/request: $0.085 ÷ 34.3 ≈ $0.00248.

Fractional requests represent averages across subscribers.

### Reconciliation with the Earlier Estimate

The earlier $0.12 estimate assumed every subscriber received:
30 daily summaries, 4 weekly analyses, and 1 deep review.

Updated packaging:
- Base subscriber AI cost: $0.07/month.
- Subscriber using one deep review: $0.12/month.
- Portfolio average at 30% review adoption: $0.085/month.

### Cost at Scale

Assuming constant usage and 30% review adoption:

| Active subscribers | Base AI cost/month | Add-on AI cost/month | Total AI cost/month |
|---|---:|---:|---:|
| 1,000 | $70 | $15 | $85 |
| 10,000 | $700 | $150 | $850 |

## Cascading Strategy

### Initial Routing

Use application rules to select the model tier by feature:

- Small: Daily summaries.
- Mid: Weekly analysis.
- Frontier: Deep preparation reviews.

Base request split:
88.24% Small / 11.76% Mid.

Portfolio request split at 30% review adoption:
87.46% Small / 11.66% Mid / 0.87% Frontier.

Percentages may not total exactly 100% due to rounding.

This is initial tier-based routing, not a validated sequential cascade.
No additional AI triage call is assumed.

### Escalation

- Define quality checks for each feature.
- Escalate failed or unresolved requests to a stronger model or human review, as appropriate.
- Count every model call, retry, and escalation in actual costs.
- Do not assume a stronger model guarantees a correct or safe answer.

### Evaluation

Test representative scenarios for:
- Factual accuracy.
- Correct use of athlete data.
- Missing or conflicting information.
- Unsupported conclusions.
- Safety and appropriate human escalation.

Confirm model assignments only after evaluation.

## Pricing Model

### Current Pricing

Pre-launch: no existing paid plan.
The $20 subscription is a planning assumption.

### Strategy

Penetration: test an accessible entry price to encourage adoption.

Whether $20 is accessible must be validated with target athletes;
no competitive price advantage has been established.

### Proposed Structure

Hybrid: subscription per athlete + usage-based add-on.

Base: $20 per athlete/month.

Includes:
- Competition readiness dashboard.
- Weight and training tracking.
- Wearable connections where available.
- Up to 30 daily AI summaries/month.
- Up to 4 weekly AI analyses/month.

Add-on: $5 per deep preparation review.

Metered unit:
One completed deep review delivered to the athlete.

Failed requests and internal retries are not billed separately.
The proposed price does not include unlimited AI usage.

### Pricing Rationale

- $20/month is the existing subscription hypothesis.
- $5/review is a new willingness-to-pay hypothesis.
- Neither price is established by AI inference cost alone.
- Validate prices against athlete value, alternatives, and total delivery costs.

### Value Proposition

Help athletes and coaches bring preparation data into one place,
understand trends, and coordinate preparation for a specific competition.

Do not promise medical benefits, a successful weigh-in,
or competition outcomes.

### Revenue Scenario

At 30% adoption and one add-on purchase per adopter/month:

Average add-on revenue/subscriber:
30% × $5 = $1.50.

Average total revenue/subscriber:
$20 + $1.50 = $21.50/month.

This is a scenario, not a revenue forecast.

## Stress Tests

Only AI cost per request changes.
Usage, subscription price, and add-on adoption remain constant.

### Base Subscription

| Metric | Baseline | AI cost +50% | AI cost ×3 |
|---|---:|---:|---:|
| Requests/user/month | 34 | 34 | 34 |
| Blended cost/request | $0.00206 | $0.00309 | $0.00618 |
| Monthly AI cost/user | $0.070 | $0.105 | $0.210 |
| Revenue/user/month | $20.00 | $20.00 | $20.00 |
| Revenue minus AI cost | $19.930 | $19.895 | $19.790 |
| Margin after AI cost only | 99.65% | 99.48% | 98.95% |

### Deep Review Add-On

| Metric | Baseline | AI cost +50% | AI cost ×3 |
|---|---:|---:|---:|
| Revenue/review | $5.00 | $5.00 | $5.00 |
| AI cost/review | $0.050 | $0.075 | $0.150 |
| Revenue minus AI cost | $4.950 | $4.925 | $4.850 |
| Margin after AI cost only | 99.00% | 98.50% | 97.00% |

### Portfolio Average

Assumes 30% of subscribers buy one review/month.

| Metric | Baseline | AI cost +50% | AI cost ×3 |
|---|---:|---:|---:|
| Average requests/subscriber/month | 34.3 | 34.3 | 34.3 |
| Average revenue/subscriber/month | $21.50 | $21.50 | $21.50 |
| Average AI cost/subscriber/month | $0.085 | $0.1275 | $0.255 |
| Revenue minus AI cost | $21.415 | $21.3725 | $21.245 |
| Margin after AI cost only | 99.60% | 99.41% | 98.81% |

Calculations use unrounded values; displayed percentages are rounded.

### Formulas

- Monthly AI cost = sum of requests × cost/request.
- Blended cost/request = total AI cost ÷ total requests.
- Average revenue = base price + adoption × add-on purchases × add-on price.
- Revenue minus AI cost = revenue − AI cost.
- Margin after AI cost only = (revenue − AI cost) ÷ revenue × 100%.

## Limitations and Excluded Costs

Not yet estimated:
- Hosting and storage.
- Wearable integration fees and maintenance.
- Payment processing.
- Direct customer support.
- Human review required to deliver the service.
- Additional routing calls, retries, and evaluation overhead.

The percentages above are not full gross margins.

Full gross margin:
(Revenue − all applicable direct service costs) ÷ revenue × 100%.

The current model does not establish profitability.
Both demand and delivery costs remain unvalidated.

## Conclusion

Under these assumptions, AI inference costs remain small
even if they triple.

The main unresolved questions are willingness to pay,
actual usage, full delivery costs, and whether deep reviews
should be bundled or sold separately.

## Next Steps

1. Validate Leader, Filler, and Killer classifications with athletes.
2. Test $20/month and $5/review willingness to pay.
3. Measure deep-review adoption and repeat purchases.
4. Select candidate models and verify current prices.
5. Measure token usage, quality, retries, and escalation rates.
6. Confirm wearable integration feasibility and costs.
7. Add all direct service costs and recalculate full gross margin.
