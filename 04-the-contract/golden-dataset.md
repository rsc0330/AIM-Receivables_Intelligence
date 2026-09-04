# Golden Dataset & Reliability Contract

## Golden Dataset Spec

| # | Input | Expected Output | Edge Case? | Judge Type |
|---|-------|----------------|-----------|-----------|
| 1 |Customer demand supports $120K/week in sales. Assembly can support $125K/week and packaging $130K/week, but machining can support only $82K/week. Packaging utilization is only 58%, and management is considering adding packaging staff. |Identify machining as the system constraint. Recommend improving or expanding machining capacity before adding resources to packaging. Explain that the recommendation is based on impact to total throughput, not local utilization. | N | rule & LLM |
| 2 |Machine A operates at 98% utilization while Machine B operates at 72%. Inventory accumulates after Machine A, but customer jobs wait an average of 3 days before Machine B. |Identify Machine B as the constraint, despite its lower utilization. Explain that the queue and delayed flow indicate the actual system constraint and avoid recommending optimization of Machine A simply because its utilization is higher. | Y| rule / LLM |
| 3 |Labor efficiency in one department falls from 90% to 72%, but company throughput increases 14%, work-in-process falls 20%, and the system constraint remains fully productive. |Do not recommend improving the department solely because labor efficiency declined. Explain that local efficiency can decrease while total system performance improves and prioritize actions based on throughput. | Y |  LLM |
| 4 |The system constraint loses 5 hours/week to changeovers. A proposed process improvement would recover 3 hours/week and cost $2,000/month. Each recovered constraint hour is expected to generate $1,500 in additional throughput, and sufficient customer demand exists. |Recommend the process improvement. Explain that recovered time at the constraint creates additional system throughput whose financial impact materially exceeds the cost of the improvement. | N | rule + LLM |
| 5 |Revenue declines 8%. Inventory, overtime, and backlog have all increased, but capacity and workflow data are missing for two critical process stages. |Do not confidently identify a system constraint. State that there is insufficient evidence, identify the missing information needed, and distinguish any possible constraint as a hypothesis rather than a conclusion. | y | rule + LLM |

**Adversarial rows included:** __
Adversarial rows included: 3 — Rows 2, 3, and 5

Coverage gaps identified by partner: Additional testing is needed for conflicting data sources, multiple simultaneous constraints, changing constraints over time, demand-constrained businesses, incorrect or incomplete user-entered data, and recommendations where customer or strategic considerations may override the mathematically optimal throughput decision.

## Confidence UX Design

**Approach:** show uncertainty / tiered confidence / human-in-loop trigger
Combine tiered confidence, visible uncertainty, and human decision control. AIM Intelligence is a decision-support product, not an autonomous decision-maker. Confidence changes how strongly AIM presents a recommendation, but AIM never automatically executes or changes a business decision.

**High confidence (>90%):**
UI + copy when you're sure:
Show one clear recommendation with the key throughput-accounting drivers, assumptions, and supporting data. Explain why the recommendation is expected to improve the business outcome. The user decides whether to act; AIM Intelligence never executes the decision automatically.

**Medium confidence (70-90%):**
What visibly softens?
Show 2–3 possible recommendations based on different assumptions or scenarios. Clearly identify which assumptions cause the recommendation to change and show the supporting data so the user can compare the options and apply their own business judgment.

**Low confidence (<70%):**
Block · escalate · human queue?
Do not make a directional recommendation. Tell the user that there is not enough reliable information to recommend a decision and identify the missing, conflicting, or unreliable data or assumptions that need to be resolved.

**User control surface:**
Y — confidence thresholds can be configured at the company/admin level within defined guardrails to reflect different levels of business risk tolerance.

See AI reasoning? Y — show the key inputs, throughput-accounting drivers, assumptions, evidence, and rationale behind the recommendation rather than exposing raw model reasoning.

Correct & override? Y — users retain final decision authority and can correct assumptions, inputs, or recommendations.

Corrections → model? Y — corrections should feed the evaluation and product-improvement process, but should not immediately retrain or change the model based on a single user correction.

## Reliability Contract

| Metric | Target | Measurement | Alert Threshold |
|--------|--------|-------------|-----------------|
| Accuracy |98%|Weekly evaluation against the golden dataset; rule-based checks for calculations and data grounding plus LLM-as-Judge for reasoning quality and recommendation support |<95% → investigate failed cases, review prompts/model changes, and restrict low-confidence recommendations until resolved |
| Hallucination rate |<0.5%; zero tolerance for fabricated customer financial or operational data |Weekly golden-dataset evaluation plus production logging for unsupported facts, invented values, or claims not grounded in source data |Any fabricated customer financial or operational value → critical review; >1% overall hallucination rate → suppress affected recommendation flows and audit |
| Latency (p95) |<5 seconds |Continuous production monitoring of end-to-end recommendation response time |>8 seconds p95 for 10 minutes → investigate model, routing, or infrastructure degradation |
| Drift velocity |<0.5% per week |4-week rolling trend of golden-dataset accuracy and hallucination results |>1% decline per week or two consecutive weeks below target → golden-dataset and model/prompt audit |

## HITL Architecture
<!-- When does a human step in? What's the escalation path? -->
AIM Intelligence is advisory only and is never permitted to automatically execute a recommendation, change customer data, or take action on the user's behalf.

High confidence: Present the recommendation, supporting reasoning, source data, and assumptions to the user.
Medium confidence: Present multiple possible recommendations based on different assumptions rather than a single definitive answer.
Low confidence: Ask the user for additional information needed to improve confidence. If confidence remains low, provide scenarios and tradeoffs instead of a prescriptive recommendation.
Critical reliability failure: Suppress the recommendation and flag the case for internal review, especially when the system detects fabricated data, incorrect calculations, unsupported reasoning, or a significant evaluation regression.
Customer organizations may configure confidence thresholds based on their risk tolerance, within minimum safety and reliability guardrails established by AIM.

The human remains the final decision-maker in all cases.

## Red-Team Findings
*What failure mode did your partner find that you missed?*
A recommendation can be factually accurate and mathematically correct but still be misleading because it is based on an incomplete or incorrect assumption about the customer's operating constraints.

For example, AIM could correctly calculate that prioritizing a specific order would maximize throughput, while missing a customer-specific constraint such as labor availability, material shortages, contractual commitments, or delivery requirements.

This means reliability cannot be measured only by calculation accuracy. AIM must clearly surface the assumptions behind its recommendation and ask for additional information or show alternative scenarios when important context is missing.
