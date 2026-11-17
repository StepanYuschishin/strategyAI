# M5 — Guardrails: BJJ Ready to Go

**Product:** BJJ Ready to Go  
**Status:** Strategy draft based on current discussion. Audit examples are hypotheses until verified with athletes, coaches, support records, or usage data.

---

## 1. Shadow AI Audit

### Goal

Find AI workarounds athletes already use around BJJ Ready to Go. Classify the gap, estimate how often it happens, and decide whether to build, partner, or monitor it.

### Evidence standard

The examples below are **hypotheses to validate**, not confirmed user findings. Replace or revise them using athlete interviews, support requests, coach conversations, public discussions, and observed workflows.

| Workaround hypothesis | Signal source to verify | Signal type | Frequency | Adjacent spend | Decision |
|---|---|---|---|---|---|
| Athletes track their weight manually in a spreadsheet or notes to reach the correct division by weigh-in | Athlete interviews; support requests | Workflow gap | Unknown | Unknown | Build candidate |
| Athletes use general-purpose AI for BJJ competition preparation | Athlete interviews; public discussions | Capability gap | Unknown | Unknown | TBD; monitor usage and unmet needs |
| Athletes check Garmin data separately from their competition-prep workflow | Athlete interviews; integration requests | Workflow gap | Unknown | Unknown | Partner candidate |
| Athletes check Apple Health data separately from their competition-prep workflow | Athlete interviews; integration requests | Workflow gap | Unknown | Unknown | Partner candidate |
| Athletes manually check tournament registration, division, and weigh-in details on event sites | Athlete interviews; event-site workflows | Workflow / trust gap | Unknown | Unknown | Partner candidate |

### Current decision hypotheses

**Build:** Explore one integrated competition-preparation workflow combining weight-to-weigh-in tracking, BJJ-specific preparation, and structured athlete-coach check-ins. Validate which pieces recur before prioritizing or committing to scope.

**Partner:** Explore consent-based Garmin and Apple Health data access, plus reliable official tournament registration and weigh-in information. Confirm access, data availability, and terms before assuming an integration is feasible.

**Ignore + monitor:** Do not build generic ChatGPT-style plans as a standalone feature. Monitor whether athletes keep using them and what they still have to do manually.

**TBD:** Decide after collecting evidence whether generic AI plans represent a recurring product gap or are simply an external tool athletes prefer to keep using.

### Measurement notes

- The current form shows adjacent spend as **$0/month** because no spend was entered. This does **not** establish that athletes spend nothing.
- Record frequency and spend only when supported by evidence; otherwise use **Unknown**.
- Do not present the five hypotheses above as five confirmed workarounds.
- Reconcile the audit row decisions with the form summary before sharing it: the current screenshots show a mismatch between the decision counts and the editable brief.

---

## 2. Governance Policy Draft

### Product and version

**BJJ Ready to Go — AI-assisted competition preparation — draft v0.1**

### Scope: what this policy covers

AI features that help BJJ athletes prepare for competitions by organizing athlete-provided training and weight information, using wearable data the athlete has chosen to connect, interpreting official event information, and supporting preparation check-ins with coaches.

The policy covers AI-generated summaries, reminders, preparation suggestions, and responses grounded in the athlete’s information and verified event sources.

### Scope: what this policy excludes

- Medical diagnosis or treatment.
- Clinical claims about health, injury, recovery, or readiness.
- Instructions for rapid weight loss, dehydration, or other potentially dangerous weight-cutting practices.
- Guaranteed competition outcomes.
- Automatic event registration, payments, or changes to an athlete’s official entry.
- High-impact health or safety recommendations without qualified human review.

### Autonomy boundaries

**May run automatically:**

- Organize athlete-provided information.
- Summarize verified tournament dates, divisions, and weigh-in details with a visible source.
- Send user-configured reminders.
- Draft non-medical preparation suggestions and check-in summaries.

**Requires human review or athlete confirmation:**

- Conflicting or incomplete event information.
- Personalized recommendations involving health, injury, recovery, nutrition, or significant weight changes.
- Recommendations that could materially change training or competition decisions.
- Any action involving registration, payment, or an official event entry.

**Never automate:**

- Medical diagnosis or treatment.
- Dangerous rapid weight-cut or dehydration instructions.
- Overriding official tournament rules.
- Submitting registration or payment without the athlete’s explicit confirmation.
- Presenting uncertain or unverified information as an official event requirement.

### Escalation triggers

Escalate to a qualified coach, clinician, or event organizer as appropriate when:

1. Official event sources conflict or do not identify the athlete’s division clearly.
2. The athlete reports injury symptoms, faintness, severe distress, or another possible health concern.
3. The request asks for rapid weight loss, dehydration, or medically risky guidance.
4. Connected data is incomplete or inconsistent enough to change the recommendation.
5. The athlete asks to speak with a human.

Do not invent numeric health or weight thresholds. Define any such thresholds with qualified sports-health professionals and review them before product use.

### Audit cadence and ownership

| Cadence | Review | Suggested owner |
|---|---|---|
| Continuous | Integration failures, source freshness, safety incidents, and service health | Engineering |
| Weekly | Sampled AI responses, athlete corrections, escalations, and reopened issues | Product Manager with coach reviewer |
| Monthly | Quality trends, recurring failure types, privacy controls, and policy gaps | Product Manager, Engineering, and qualified reviewer |
| After a material change | Regression review after model, prompt, retrieval, routing, or policy changes | Product and Engineering |

Assign named people before launch. “The team” alone is not an owner.

### Regulatory exposure and controls

**Regimes to assess:** GDPR and applicable health-data requirements; assess whether and how the EU AI Act applies to the product and each use case. Obtain qualified legal review before assigning a regulatory risk category.

**Risk tier:** Not assigned in this draft. Do not select a tier solely from the product description.

**Proposed controls:**

- Collect only data needed for the stated feature.
- Obtain clear consent before connecting wearable or health-related data.
- Explain data use, retention, deletion, and access in user-facing terms.
- Restrict access to sensitive data and keep appropriate audit records.
- Review vendor data handling and retention before sending sensitive information to an AI provider.
- Do not use personal health data for model training by default.
- Keep official event information distinguishable from AI-generated interpretation.

### Optional agent topology

No autonomous agent workflow is assumed to be shipped today. If implemented:

- **Event Information Retriever:** Can read approved event sources; cannot change an athlete’s registration; returns source and retrieval time.
- **Wearable Data Connector:** Reads only athlete-authorized data; cannot expand access or infer a diagnosis.
- **Preparation Assistant:** Can draft non-medical suggestions; cannot provide diagnosis, dangerous weight-cut instructions, or make official event changes.
- **Human Reviewer:** Coach, qualified health professional, or event organizer reviews cases within their expertise.

---

## 3. Compounding System Designer

### Goal

Map which product loops learn from use, which only scale, and where missing handoffs prevent learning from improving the product.

### Loop 1: Recursive Learning

**Input:** With consent, athlete corrections, coach overrides, explicit feedback, and observed preparation outcomes.

**Output:** Human-reviewed cases that may become evaluation examples, product changes, or updated guidance.

**Does it compound?** Potentially. Mark **Yes** only after validated feedback changes the product and improves measured outcomes.

**Current status:** Missing / unverified. No confirmed process has been described that consistently turns corrections into reviewed tests and shipped improvements.

### Loop 2: Cross-Domain Transfer

**Input:** Athlete-authorized training and wearable data, athlete-entered weight trends, competition date, division rules, and verified event details.

**Output:** Competition-specific context that connects preparation, weigh-in planning, and relevant event information.

**Does it compound?** Potentially, if combining these domains improves future recommendations beyond what each data source provides alone.

**Current status:** Missing / unverified. The product concept includes these data domains, but the working integrations and demonstrated transfer have not been confirmed here.

### Loop 3: Network Intelligence

**Input:** Only appropriately aggregated and consented patterns across athletes, teams, coaches, or events.

**Output:** Optional cohort-level insights, such as common preparation patterns or event-planning needs.

**Does it compound?** Potentially, if more participation improves useful insights for other users without exposing an individual’s sensitive information.

**Current status:** Missing / unverified. Do not claim a network effect or use sensitive cohort data without privacy, consent, and minimum-volume safeguards.

### Broken loop identified

**Hypothesis:** Athlete corrections, coach feedback, and preparation outcomes may not reliably flow into a reviewed product-learning process.

**Why this matters:** Collecting feedback alone does not improve a product. A loop compounds only when useful signals are captured, reviewed, turned into a safe product or evaluation change, and checked against later results.

### Fix plan

1. Provide a clear way for athletes and coaches to correct or flag a recommendation.
2. Record the relevant context and the reason for the correction, with consent and appropriate data minimization.
3. Have a named product owner and qualified reviewer examine recurring or safety-relevant cases.
4. Add validated cases to the evaluation set; do not treat every user correction as ground truth.
5. Update the product’s prompts, retrieval, routing, rules, or UX where appropriate.
6. Re-test against the evaluation set before release.
7. Track whether the change improves correct, useful outcomes without increasing safety issues or unnecessary escalations.

### Context connectivity

**Intended flow:**  
Athlete-authorized wearable and training data + athlete-entered weight information + verified event details → athlete-specific preparation context → AI-generated draft or summary → athlete/coach review where appropriate → consented correction or outcome signal → reviewed evaluation case → product update.

**Potential silos to validate:**

- Wearable data may remain separate from BJJ-specific training and event context.
- Tournament information may be distributed across event pages and not consistently structured.
- Coach feedback may remain in conversations rather than reaching a reviewable product workflow.
- Product feedback may not reach the people maintaining prompts, retrieval, routing, and evaluations.

### Freeze test

If the underlying model stayed unchanged for about three months, would the product still improve for athletes?

If yes, the durable advantage may come from trusted workflow, useful integrations, verified event context, coach relationships, or athlete experience rather than model updates alone.

If no, identify which real, safe learning loop could improve the product. This is a diagnostic question, not proof that a moat already exists.

---

## 4. Important distinctions

- A third-party model is controlled by its provider. A golden dataset does not automatically train or change that model.
- Product improvements may come from changes to prompts, retrieval, routing, product rules, UX, or evaluations.
- A golden dataset is a set of reviewed test examples and expected outcomes. It is not automatically the live product’s memory.
- An LLM judge can help score outputs against a rubric, but it needs calibration against reviewed examples and human expertise.
- A router chooses a processing path or model. It is a separate runtime function from an offline evaluator, though products may add runtime checks when justified.
- User feedback is a signal, not automatically ground truth. Review it before using it to change product behavior.

---

## 5. Decisions still needing evidence

1. Which of the five workaround hypotheses have athletes actually reported or demonstrated?
2. How often does each workaround occur, and what adjacent spend can be verified?
3. Which proposed build, partner, and ignore decisions match the actual audit rows?
4. Which wearable and tournament data sources are technically and contractually accessible?
5. Which preparation recommendations need coach review, and which require qualified health expertise?
6. What consent, retention, privacy, and regulatory controls apply to the actual launch markets?
7. Which feedback loop can be implemented and measured first?
