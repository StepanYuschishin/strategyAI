# BJJ Athlete Training Strategy

## Strategy at a Glance

Build a trusted training companion for Brazilian Jiu-Jitsu athletes that connects training, competition preparation, weight management, and coach support. Focus on the workflows athletes currently piece together themselves, while partnering for health and tournament data that the product should not recreate.

## Product Direction

Help athletes prepare consistently for training and competition with structured, sport-specific workflows and useful context from their existing tools.

Prioritize recurring athlete needs over generic AI-generated plans. Keep coaches involved in meaningful check-ins and make competition preparation specific to BJJ.

## Shadow AI Audit

Five user-side workarounds were identified:

1. Weight-to-weigh-in tracking.
2. BJJ-specific competition preparation.
3. Structured athlete-coach check-ins.
4. Garmin data access.
5. Apple Health data access.
6. Official tournament registration and weigh-in data.
7. Generic ChatGPT-generated plans used outside the product.

The audit summary recorded five workarounds, one build candidate, three partner candidates, and no ignore decisions, with workflow gaps as the dominant signal. The action plan groups weight tracking, competition preparation, and coach check-ins as potential build candidates, pending validation of how often they recur.

## Build

Potentially bring these workflows into the product:

- Weight-to-weigh-in tracking.
- BJJ-specific competition preparation.
- Structured athlete-coach check-ins.

Validate which workarounds recur most often before prioritizing implementation.

## Partner

Explore official integrations for:

- Garmin and Apple Health data.
- Tournament registration and weigh-in data.

## Ignore and Monitor

Do not treat generic ChatGPT-generated plans as a standalone product feature yet. Monitor whether athletes continue using them and which parts of their workflow remain manual.

## Governance and Risk

Review data handling for health, weight, and athlete information. Define access controls, human oversight, escalation paths, and a regular review cadence before expanding automated recommendations.

## Compounding System

Map and validate the product's learning loops before claiming that usage improves the system. For each loop, document its input, output, whether it compounds, and whether it is active, broken, or missing.

Candidate loops to assess:

- **Recursive learning:** athlete corrections and feedback inform better training or competition-preparation guidance.
- **Cross-domain transfer:** training, health, and competition context improve recommendations across workflows, subject to user consent and data permissions.
- **Network intelligence:** aggregated insights improve the product across athletes or coaches only where privacy, consent, and appropriate safeguards allow it.

## Open Validation

- Which workarounds appear most frequently in athlete interviews and support requests?
- Which data sources can be accessed reliably and with user consent?
- What should remain coach-led rather than automated?
- Which feedback signals can safely and measurably improve the product?
