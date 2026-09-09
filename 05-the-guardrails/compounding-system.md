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

**Scope:**
**Autonomy boundaries:**
**Escalation triggers:**
**Audit cadence:**
**Regulatory exposure (EU AI Act / other):**

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |

**Total tools found:**
**Tools after triage:**
**Estimated hidden spend:**
