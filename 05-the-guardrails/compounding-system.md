# BJJ Ready to Go — Compounding System

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|---|---|---|---|---|
| Recursive Learning | Athlete corrects a preparation recommendation and records actual weight, training, and recovery | The next recommendation uses that correction and its outcome | Potentially — if corrections are stored and reused | Proposed; not validated |
| Cross-Domain Transfer | Weight trend, training load, recovery signals, and competition date | A preparation recommendation that considers these signals together | Potentially — if combined signals improve decisions beyond any single source | Proposed; not validated |
| Network Intelligence | Consented, comparable preparation histories and competition outcomes across athletes | Patterns that help future athletes in similar situations | Potentially — if more athletes produce better, validated recommendations | Proposed; not validated |

### Broken loop to fix first

**Break:** An athlete corrects a recommendation, but the product does not retain why it was wrong. The same mistake can happen again.

**Fix:** Save the correction, relevant context, and eventual outcome. Test whether using them improves the next recommendation.

## Context Connectivity

The relevant information may sit in separate places: Garmin or other wearables, weight logs, competition details, training records, and athlete feedback.

Connect these records to one athlete and one competition preparation cycle. A recommendation should be traceable to the signals and rules that produced it.

## Three-Month Freeze Test

Assume the underlying AI model does not improve for three months. Does BJJ Ready to Go get better because it has learned from verified corrections and preparation outcomes?

**Current answer:** Unknown. We need to compare later recommendations with earlier ones on similar cases. More data or more users alone would not prove compounding.
