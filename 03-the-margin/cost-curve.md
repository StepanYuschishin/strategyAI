# Cost Curve — BJJ Ready to Go

## Packaging Decision

These classifications are hypotheses to validate with athletes.

| Category | Feature | Reason |
|---|---|---|
| Leader | Competition readiness dashboard combining weight, training, recovery, and competition date | The main reason athletes would subscribe |
| Filler | AI daily summaries and weekly trend explanations | Adds convenience and helps athletes interpret their data |
| Killer | On-demand deep competition preparation review | Potentially costly, occasional analysis that may not be needed by everyone |

### Killer Usage and Packaging

- Killer usage: Unknown.
- Planning hypothesis: 30% of monthly active subscribers request a deep review.
- This percentage measures users adopting the feature, not its share of requests.
- Course heuristic: If adoption is below 70%, consider an add-on.
- Initial decision: Bundle the dashboard, daily summaries, and weekly analysis at $20/month. Offer deep reviews as a paid add-on.
- Add-on price: Not yet determined.
- Validate adoption, willingness to pay, and actual delivery cost before confirming packaging.

## Assumptions

- Base subscription: $20 per user/month.
- Wearable sources may include Garmin, WHOOP, and Apple Watch.
- Base usage: 30 daily summaries and 4 weekly analyses per user/month.
- Deep review: 1 request per adopting user/month.
- Assumed deep-review adoption: 30%.
- AI prices below are illustrative, not verified provider prices.
- Data imports and basic calculations use regular software rather than LLM calls.

## Cost Model

### Per-Feature Costs

| Feature | Complexity | Model tier | Cost/request | Requests per adopting user/month |
|---|---|---|---:|---:|
| Daily summary | Simple | Small | $0.001 | 30 |
| Weekly analysis | Medium | Mid | $0.010 | 4 |
| Deep preparation review | Complex | Frontier | $0.050 | 1 |

### Base Subscription

Monthly requests per subscriber:
30 + 4 = 34.

Monthly AI cost per subscriber:
(30 × $0.001) + (4 × $0.010) = $0.07.

Blended cost per request:
$0.07 ÷ 34 ≈ $0.00206.

| Tier | Requests/month | Volume share | Weighted cost/request |
|---|---:|---:|---:|
| Small | 30 | 88.24% | $0.00088 |
| Mid | 4 | 11.76% | $0.00118 |
| Blended | 34 | 100% | $0.00206 |

### Add-On and Portfolio Average

- AI cost per deep review: $0.05.
- At 30% adoption and one review per adopter:
  average add-on AI cost per subscriber = 30% × $0.05 = $0.015.
- Average total AI cost per subscriber:
  $0.07 + $0.015 = $0.085.
- Average total requests per subscriber:
  34 + (30% × 1) = 34.3.
- Portfolio blended cost/request:
  $0.085 ÷ 34.3 ≈ $0.00248.

Fractional requests represent an average across subscribers.

### Reconciliation with the Earlier Estimate

The earlier $0.12 estimate assumed every subscriber received
30 summaries, 4 weekly analyses, and 1 deep review each month.

The updated packaging separates the deep review:
- Base subscription AI cost: $0.07.
- Subscriber using one deep review: $0.12.
- Portfolio average at 30% review adoption: $0.085.

### Cost at Scale

Assuming the same usage and 30% deep-review adoption:

| Active subscribers | Base AI cost/month | Add-on AI cost/month | Total AI cost/month |
|---:|---:|---:|---:|
| 1,000 | $70 | $15 | $85 |
| 10,000 | $700 | $150 | $850 |

## Cascading Strategy

### Initial Routing

Use application rules to route requests directly:

- Small model: Daily summaries.
- Mid-tier model: Weekly trend analysis.
- Frontier model: Deep competition preparation reviews.

Base request split:
88.24% small / 11.76% mid.

Portfolio request split at 30% review adoption:
87.46% small / 11.66% mid / 0.87% frontier.
Percentages may not total exactly 100% due to rounding.

Specific providers and models have not yet been selected.
This is tier-based routing, not a validated sequential cascade.

### Escalation and Quality

- Escalate when a request fails defined quality checks.
- Include every retry and additional model call in actual costs.
- Use human review where appropriate.
- Test factual accuracy, missing-data handling, and safety.
- More expensive models do not automatically guarantee better results.

## Stress Tests

### Base Subscription

Usage and subscription price remain unchanged.
Only AI cost per request increases.

| Metric | Baseline | AI cost +50% | AI cost ×3 |
|---|---:|---:|---:|
| Requests/user/month | 34 | 34 | 34 |
| Blended cost/request | $0.00206 | $0.00309 | $0.00618 |
| Monthly AI cost/user | $0.07 | $0.105 | $0.21 |
| Revenue/user/month | $20.00 | $20.00 | $20.00 |
| Revenue minus AI cost | $19.93 | $19.895 | $19.79 |
| Margin after AI cost only | 99.65% | 99.475% | 98.95% |

Calculations use unrounded values.

### Add-On Sensitivity

| Metric | Baseline | AI cost +50% | AI cost ×3 |
|---|---:|---:|---:|
| AI cost per deep review | $0.05 | $0.075 | $0.15 |

Add-on revenue and margin cannot be calculated until its price is set.

### Formulas

- Monthly AI cost = sum of requests × cost/request.
- Blended cost/request = total AI cost ÷ total requests.
- Revenue minus AI cost = revenue − AI cost.
- Margin after AI cost only = (revenue − AI cost) ÷ revenue × 100%.

## Limitations

These are planning estimates, not measured economics.

Excluded costs:
- Hosting and storage.
- Wearable integrations and associated fees.
- Payment processing.
- Direct customer support.
- Routing overhead, retries, and additional evaluation calls.

The percentages above are not full gross margins.
Full gross margin requires all applicable direct service costs.

## Conclusion

Under these assumptions, AI inference costs are small relative
to the proposed $20 subscription, even if they triple.

The add-on decision remains provisional: actual adoption,
willingness to pay, and measured costs may justify bundling instead.

## Next Steps

1. Validate the Leader, Filler, and Killer classifications with athletes.
2. Measure deep-review adoption and willingness to pay.
3. Select models and verify current token prices.
4. Measure token usage, quality, retries, and escalation rates.
5. Add other direct costs and calculate full gross margin.
