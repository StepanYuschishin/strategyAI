# Cost Curve — BJJ Ready to Go

## Cost Model

Planning assumptions per active athlete per month:
- 30 daily summaries.
- 4 weekly analyses.
- 1 complex competition preparation review.
- Total: 35 requests.

Costs are illustrative assumptions, not verified provider prices.

| Feature | Complexity | Model tier | Cost/request | Requests/month | Volume share | Weighted cost/request |
|---|---|---|---:|---:|---:|---:|
| Daily summary | Simple | Small | $0.001 | 30 | 85.7% | $0.00086 |
| Weekly analysis | Medium | Mid | $0.010 | 4 | 11.4% | $0.00114 |
| Complex preparation review | Complex | Frontier | $0.050 | 1 | 2.9% | $0.00143 |
| Blended | | | | 35 | 100% | $0.00343 |

Monthly AI inference cost per active athlete:
(30 × $0.001) + (4 × $0.010) + (1 × $0.050) = $0.12.

Excludes hosting, storage, wearable integrations, support, retries, and routing overhead.

## Cascading Strategy

- Triage: Route by feature type using application rules, without an extra model call.
- Small model: Daily summaries.
- Mid-tier model: Weekly analysis.
- Frontier model: Complex preparation reviews.
- Expected routing split: 
