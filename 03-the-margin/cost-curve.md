# Cost Curve — BJJ Ready to Go

## Assumptions

- Subscription price: $20 per user/month.
- Monthly usage per active user: 30 daily summaries, 4 weekly analyses, and 1 complex preparation review.
- Total: 35 AI requests per user/month.
- Usage, model assignments, and AI costs are planning assumptions, not measured results or verified provider prices.
- Wearable sources may include Garmin, WHOOP, and Apple Watch.
- Data imports and basic calculations use regular software rather than LLM calls.

## Cost Model

| Feature | Complexity | Model tier | Cost/request | Requests/month | Volume share | Weighted cost/request |
|---|---|---|---:|---:|---:|---:|
| Daily summary | Simple | Small | $0.001 | 30 | 85.7% | $0.00086 |
| Weekly analysis | Medium | Mid | $0.010 | 4 | 11.4% | $0.00114 |
| Complex competition preparation review | Complex | Frontier | $0.050 | 1 | 2.9% | $0.00143 |
| Blended | | | | 35 | 100% | $0.00343 |

### Calculations

- Total requests: 30 + 4 + 1 = 35.
- Volume share: feature requests ÷ 35.
- Weighted cost/request: feature cost/request × its volume share.
- Monthly AI cost: (30 × $0.001) + (4 × $0.010) + (1 × $0.050) = $0.12.
- Blended cost/request: $0.12 ÷ 35 ≈ $0.00343.

Calculations use unrounded values; displayed figures are rounded.

### Cost at Scale

Assuming the same usage per active user:

| Active users | Monthly AI inference cost |
|---:|---:|
| 1,000 | $120 |
| 10,000 | $1,200 |

## Cascading Strategy

### Initial Routing

Route directly by feature type using application rules:

- Small model: daily summaries.
- Mid-tier model: weekly analysis.
- Frontier model: complex preparation reviews.

Expected routing split: 85.7% small / 11.4% mid / 2.9% frontier.

Specific providers and models have not yet been selected. This is initial tier-based routing, not a validated sequential cascade.

### Escalation

If a model cannot complete a task reliably, escalate to a stronger model or human review, as appropriate. Count every model call in the request's actual cost.

The baseline assumes one model call per request. Additional triage calls, retries, and escalations will increase costs.

### Validation

Test each tier on representative BJJ scenarios before confirming assignments. Evaluate factual accuracy, handling of missing or conflicting data, and safety. A stronger model does not replace qualified human review where needed.

## Stress Tests

The stress scenarios increase AI cost per request while keeping usage and subscription revenue unchanged.

| Metric | Baseline | AI cost +50% | AI cost ×3 |
|---|---:|---:|---:|
| Requests per user/month | 35 | 35 | 35 |
| Blended cost per request | $0.00343 | $0.00514 | $0.01029 |
| Monthly AI cost per user | $0.12 | $0.18 | $0.36 |
| Revenue per user/month | $20.00 | $20.00 | $20.00 |
| Revenue minus AI cost | $19.88 | $19.82 | $19.64 |
| Margin after AI cost only | 99.4% | 99.1% | 98.2% |

### Formulas

- Monthly AI cost = requests × blended cost per request.
- Revenue minus AI cost = monthly revenue − monthly AI cost.
- Margin after AI cost only = (revenue − AI cost) ÷ revenue × 100%.

### Conclusion

Under these assumptions, AI inference costs remain small even if they triple. This does not establish overall profitability or validate the $20 subscription price.

## Excluded Costs

Not yet estimated:

- Hosting and storage.
- Wearable integrations and any associated fees.
- Payment processing.
- Direct customer support.
- Additional model calls, retries, and evaluation overhead.

Full gross margin must include all applicable direct costs of delivering the service. The percentages above are not full gross margins.

## Next Steps

1. Select candidate models and verify current prices.
2. Measure input/output tokens on representative requests.
3. Test quality and record retry and escalation rates.
4. Validate usage frequency and willingness to pay with athletes.
5. Add other direct service costs and recalculate full gross margin.
