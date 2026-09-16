# Compounding System Design

## Feedback Loops

 Loop | Input | Output | Compounds? | Status |
|---|---|---|---|---|
| Recursive Learning | User actions, corrections, overrides, recommendation acceptance/rejection, and actual business outcomes | Better personalized recommendations, predictions, alerts, and next-best actions | Y | Missing / Early |
| Cross-Domain Transfer | Connected Sales, Production, Purchasing, Inventory, Bookkeeping, and Throughput data | Decisions informed by end-to-end business context rather than individual modules | Y | Broken / Being Designed |
| Network Intelligence | Aggregated and appropriately anonymized patterns across AIM customers and industries | Benchmarks, pattern detection, and improved recommendations across similar businesses | Y | Missing |

### Broken Loop

AIM recommendation → user decision/correction → business outcome → **learning is not systematically captured**

**Fix:** Build a structured feedback event layer that connects each recommendation with the user's response and eventual business outcome. Use this information for evaluation, personalization, and future recommendations.

## Context Connectivity

Knowledge currently exists across Sales, Production, Purchasing, Inventory, Bookkeeping, and Reporting, but the business context between these domains is not yet consistently connected.

AIM's opportunity is to create shared context linking:

Customer → Product → Sales Order → Work Order → Production Resource/Constraint → Shipment → Invoice → Payment → Financial/Throughput Outcome

This cross-domain context could become a core proprietary advantage for AIM Intelligence.

## Freeze Test

If frontier models stopped improving for three months, AIM Intelligence today would likely improve very little.

This indicates AIM is not yet truly compounding.

The target architecture is:

AIM Usage → Business Context → Recommendation → User Decision → Business Outcome → Feedback/Evaluation → Better AIM Recommendation

When this loop functions, AIM can continue improving even when the underlying frontier model does not.

## Governance Policy

Scope:
Applies to AIM Intelligence features that use AI to analyze customer and operational data, identify constraints or opportunities using Throughput Accounting principles, generate scenarios, and provide recommendations to users.

Autonomy boundaries:
AIM Intelligence is advisory and decision-support only. It may analyze data, identify patterns, explain reasoning, surface assumptions, and present multiple possible recommendations. It may not automatically execute decisions, modify accounting or operational records, initiate transactions, communicate with customers, or make irreversible business changes. Final decision authority remains with the user.

Escalation triggers:
Human review is required when confidence falls below the customer-configured threshold; required data is missing, conflicting, or unreliable; recommendations could have significant financial or operational impact; the AI produces unsupported or potentially hallucinated claims; results materially differ from established patterns; or the requested action falls outside the system's approved decision-support scope.

Audit cadence:
Monitor reliability, hallucination, confidence, latency, and drift metrics on an ongoing basis, with a formal governance review at least quarterly. Conduct an additional review after significant model, prompt, data, architecture, or policy changes and after any material AI incident.

Regulatory exposure (EU AI Act / other):
Core AIM Intelligence is expected to have relatively limited EU AI Act exposure when used strictly as business decision-support with meaningful human oversight and no autonomous decision execution. However, classification should be reassessed if the product is used for regulated or high-risk purposes such as employment decisions, creditworthiness decisions involving individuals, or other Annex III use cases. Users should be clearly informed when they are interacting with AI, and appropriate documentation, monitoring, auditability, data governance, and human oversight should be maintained. Privacy regulations such as GDPR may also apply when personal data is processed.

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|------------|----------|
| Unapproved public LLMs (ChatGPT, Claude, Gemini, etc.) used with AIM/customer data | Individual employees | H | govern |
| AI meeting / transcription tools used for customer or internal meetings | Sales / Support / Product | M | govern |
| Unapproved AI automation tools with ability to update records or trigger workflows | Individual employees / Operations | H | kill |

**Total tools found:** 3  
**Tools after triage:** 2  
**Estimated hidden spend:** ~$100–$200/month
