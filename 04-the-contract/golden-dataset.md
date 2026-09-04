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

## Reliability Contract

| Metric | Target | Measurement | Alert Threshold |
|--------|--------|-------------|-----------------|
| Accuracy | | | |
| Hallucination rate | | | |
| Latency (p95) | | | |
| Drift velocity | | | |

## HITL Architecture
<!-- When does a human step in? What's the escalation path? -->

## Red-Team Findings
*What failure mode did your partner find that you missed?*
