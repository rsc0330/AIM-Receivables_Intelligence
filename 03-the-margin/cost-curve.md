# Cost Curve & Pricing Strategy

## Cost Model

**Baseline assumptions:** 20 AI requests per active user/month, approximately $0.10 blended cost per request, and $100/month current AIM revenue.

| Cost Category                | Per-User/Month | Notes                                                                                                          |
| ---------------------------- | -------------- | -------------------------------------------------------------------------------------------------------------- |
| Inference (primary model)    | $1.20          | Main model used for business analysis, throughput insights, and recommendations                                |
| Inference (cascading/triage) | $0.30          | Lower-cost model handles simpler classification, summarization, and routing before escalating complex requests |
| Infrastructure               | $0.30          | APIs, orchestration, monitoring, compute, and supporting services                                              |
| Data/storage                 | $0.20          | Storage, retrieval, embeddings/context, and operational data needed for AI analysis                            |
| Human-in-the-loop            | $0.00          | Customer reviews/approves recommendations; no AIM employee review assumed in the initial model                 |
| **Total AI COGS**            | **$2.00**      | Based on approximately 20 requests/month at a blended cost of $0.10/request                                    |

## Cascading Strategy

**Triage model:** Lower-cost, fast model for classification, summarization, simple explanations, and determining whether deeper analysis is required.

**Frontier model:** Higher-capability reasoning model used for complex throughput analysis, cross-functional recommendations, constraint analysis, and higher-risk decisions.

**Routing rule:** Route routine explanations and simple analysis to the triage model. Escalate to the frontier model when a request requires analysis across multiple business areas, conflicting constraints, scenario evaluation, or a recommendation that could materially affect production or financial decisions.

**Expected cascade ratio:** Approximately **80% triage / 20% frontier** initially. Monitor actual usage and adjust as AIM learns which requests truly require the more expensive model.

## Pricing Model

**Current pricing:** $100/month flat fee for the AIM desktop application.

**Proposed AI pricing:** Keep basic AI explanations and low-cost assistance bundled with AIM. Offer advanced **AIM Intelligence** capabilities—such as continuous throughput analysis and operational recommendations—as a premium add-on. Meter or limit high-volume automated actions if usage creates significant variable cost.

**Model:** **Hybrid**

Base subscription/access pricing + bundled basic AI + premium AI capability and/or usage-based pricing for high-cost automation.

## Stress Tests

| Scenario                         | Impact on Margin                                                                                                                            | Response                                                                                                                              |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Inference costs 3x               | AI COGS increases from approximately $2 to $5/user/month. Gross margin on $100 revenue remains approximately 95% before other product COGS. | Maintain model cascading, optimize prompts/context, monitor model costs, and preserve ability to switch providers/models.             |
| Heaviest segment doubles         | At 40 requests/month, AI COGS increases from approximately $2 to $4/user/month. Margin remains approximately 96% before other product COGS. | Track usage by customer. Introduce usage thresholds or premium tiers if a small group begins consuming disproportionate AI resources. |
| Model provider raises prices 50% | Estimated AI COGS increases from approximately $2.00 to $2.75/user/month, leaving approximately 97.25% margin on the AI cost component.     | Maintain provider portability, route more requests to lower-cost models, and revisit pricing if increases become structural.          |

## Board One-Pager

**Before (traditional SaaS):**
AIM generates approximately $100/month in flat subscription revenue. Customer usage has relatively little impact on marginal software delivery cost.

**After (AI-enabled):**
AIM retains its $100/month core subscription while introducing AI capabilities that create variable usage costs. Basic AI can be bundled because expected AI COGS is low. Higher-value AIM Intelligence capabilities can increase ARPU through an add-on, while high-volume automation can be usage-based to protect margins.

**Net margin shift:**
If basic AI is bundled with no price increase, the current model introduces approximately **$2/user/month of incremental AI COGS**, or roughly **2 percentage points of margin pressure** on a $100 subscription. Advanced AI add-ons and usage-based pricing can offset this cost and potentially increase overall ARPU and gross profit.
