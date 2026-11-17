## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| Recursive Learning | Athlete corrections to weight targets, training recommendations, and recovery guidance; weigh-in results and post-competition feedback. | With athlete consent, reviewed corrections become labeled examples for improving weight-readiness estimates and recommendations; approved cases are added to the evaluation set. | Y | missing |
| Cross-Domain Transfer | Competition schedule and rules, athlete weight trends, training load, recovery signals, and wearable data. | A more relevant preparation plan that connects competition deadlines, weight readiness, training, and recovery for that athlete. | N | missing |
| Network Intelligence | Opt-in participation and verified, aggregated signals from athletes and competitions. | Better cohort-level benchmarks for preparation and weight trends, without exposing individual athletes’ data. | N | missing |

**Broken loop identified by partner:** Recursive Learning — athlete corrections and actual weigh-in outcomes are not yet captured in a consistent, reviewed feedback loop.
**Fix plan:** Add a post-weigh-in check-in for planned vs. actual weight and a way to correct recommendations. With consent, review and label the feedback, then add suitable cases to the evaluation set before using them to improve recommendations. Owner: Product.

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->

**How knowledge flows:** Competition rules and schedules, athlete check-ins, and consented wearable data feed the athlete’s preparation plan. Coaches and athletes can correct it; reviewed corrections inform product evaluations.

**Where it silos:** Competition information, wearable data, and athlete feedback come from separate sources. Without consent, consistent formats, and review, they cannot safely be combined into a reliable learning loop.


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

<!-- Governance Policy, BJJ Ready to Go — Athlete Preparation Assistant v1 -->

## Governance Policy

**Scope:** AI-generated competition preparation guidance using athlete-provided training and weight logs, connected wearable data, and public tournament information. Includes data summaries, weight trend estimates, reminders, and preparation suggestions. Athletes review and choose whether to follow suggestions. Excludes: Medical diagnosis or treatment, injury clearance, guaranteed competition outcomes, and instructions for rapid weight cutting, dehydration, or ignoring concerning symptoms.

**Autonomy boundaries:** Summarize synced training, sleep, and recovery data, auto. Show weight trends and estimate progress toward the athlete’s stated division, auto. Recommend changes to training or weight-management plans, human approval required. Give medical advice, diagnose symptoms, or recommend dehydration or rapid weight-cut tactics, never auto. Change competition registration, weight class, or event booking, never auto.

**Escalation triggers:** 1. The athlete reports fainting, chest pain, severe dehydration, injury, or another concerning symptom: stop weight-cut guidance and direct them to a qualified medical professional. 2. The requested weight change appears aggressive or the timeline is unclear: do not suggest a cut plan; recommend speaking with a qualified coach or sports dietitian. 3. Tournament date, weigh-in time, division, or weight limit is missing or conflicting: show the conflicting sources and ask the athlete to confirm with the organizer. 4. Wearable or weight data is missing, stale, or inconsistent: label the information incomplete and ask the athlete to verify it before using it for guidance. 5. The athlete asks for a human review or says the guidance is wrong.

**Audit cadence:** Real-time, Data-sync failures, stale readings, and safety escalation events (Engineering on-call). Weekly, A sample of AI guidance, athlete corrections, escalations, and reported issues (Product manager). Monthly, Weight-guidance safety, event-information accuracy, user complaints, and recurring failure patterns (Product manager with a qualified BJJ coach or sports dietitian). Weekly, Changes to prompts, models, data sources, safety rules, and escalation behavior against the approved test cases (Product and engineering).

**Regulatory exposure (EU AI Act / other):** GDPR and applicable data-protection requirements for personal and potentially health-related data. Confirm applicable obligations with privacy counsel before launch.. Risk tier: limited. Controls: Collect only data needed for the preparation features; obtain clear consent for wearable connections; let athletes disconnect integrations and delete their data; label estimates and data freshness; do not present the product as medical advice; block dangerous rapid-cut or dehydration guidance; require athlete confirmation before changing plans; log AI recommendations, source data, corrections, and escalations; provide a clear route to a qualified human..

## Agent Topology

No autonomous agents in v1. The product may summarize data, show trends, and draft preparation suggestions. It cannot change training or weight plans, register the athlete for an event, change their division, contact anyone, or take medical action. The athlete decides what to follow; safety concerns are directed to a qualified professional.

Shadow AI Audit (user-side), Module 5

## Discover, User-Side Workarounds
- Athletes track daily weight and target weigh-in in a spreadsheet | source: Support ticket | signal: Workflow gap | freq: M | spend: $0/mo | decision: TBD
- Athletes check Garmin or Apple Health separately, then interpret readiness alongside training notes | source: Support ticket | signal: Capability gap | freq: M | spend: $0/mo | decision: Partner
- Athletes paste weight, training history, and competition date into ChatGPT for a prep plan | source: Support ticket | signal: Capability gap | freq: H | spend: $0/mo | decision: Build
- Athletes use WhatsApp or direct messages with their coach for weight and training check-ins | source: Support ticket | signal: Trust gap | freq: M | spend: $0/mo | decision: Partner
- Athletes check tournament pages and calendars manually for registration and weigh-in deadlines | source: Support ticket | signal: Workflow gap | freq: M | spend: $0/mo | decision: Partner

## Pattern Assessment
- Workarounds found: 5
- Build candidates: 1
- Partner candidates: 3
- Ignore decisions: 0
- Adjacent spend: $0/mo
- Dominant signal: Workflow gap

## Action Plan
### Build
Potential build candidates: weight-to-weigh-in tracking, BJJ-specific competition prep, and structured athlete-coach check-ins. Validate which workarounds recur before prioritizing.

### Partner
Garmin and Apple Health data access; official tournament registration and weigh-in data.

### Ignore + Monitor
Generic AI-generated training plans as a standalone feature. Monitor whether athletes keep using them and what they still have to do manually.

## Roadmap Brief
Based on your audit: 5 user-side workarounds discovered.
Decisions: 1 build · 3 partner · 0 ignore · 1 TBD.
Estimated adjacent spend: $0/mo across surveyed users.
Dominant signal: Workflow gap.

Recommended next step: Workflow gaps dominate, your users are stitching your product into multi-step pipelines. Strongest near-term move is partner integrations with the AI tools they already chain in.

Sequence the Build column by frequency × strategic relevance. Confirm Partner candidates with the external tools' partnership teams. Re-run this audit each quarter, workarounds shift fast.

