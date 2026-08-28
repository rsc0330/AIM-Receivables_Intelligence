# Kill Switch Audit

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | No production provider selected; prototype currently uses simulated AI behavior.| M |Define at least two approved model providers and document AIM's provider-independent model requirements.|
| **Abstraction** |No formal AI abstraction layer exists yet. | H |Route all future AI requests through an AIM-owned Intelligence Service rather than embedding vendor APIs directly into product features.  |
| **Routing** |No provider/model routing capability currently exists. | H |Implement configuration-based model routing with primary and fallback providers. |
| **Eval** |Business success metrics exist, but no reusable cross-model evaluation suite has been created. | H |Build an initial benchmark set of AIM Intelligence scenarios with expected recommendations and scoring criteria. |
|

## Portability Score
<!-- Ready / Partial / Locked -->
Partial
AIM is not technically locked in yet, but it is also not 48-hour swap ready because the abstraction, routing, and model-evaluation infrastructure does not exist.
## Actions
**This week:** Define AIM's provider-independent model requirements and identify a primary and fallback provider.
**This month:** Build an AIM Intelligence abstraction and routing layer so application features never directly depend on a specific model vendor.
**This quarter:** Build an AIM Evaluation Suite using representative financial, operational, and Throughput Accounting scenarios so replacement models can be tested quickly against the same quality, safety, latency, and cost standards.


## If [primary vendor] doubles pricing tomorrow:
<!-- What's your 48-hour response? -->
Route appropriate workloads to the approved secondary provider, run the replacement model through the AIM Evaluation Suite, validate performance against defined thresholds, and switch production routing without rebuilding product features.

## If [primary vendor] ships a competing product:
<!-- What's defensible that they can't replicate? -->
Reduce or replace dependency on that provider. AIM retains ownership of its Throughput Accounting decision logic, workflow context, evaluation framework, recommendation history, and business outcome data. The underlying model remains a replaceable infrastructure component rather than the source of AIM's differentiation.
