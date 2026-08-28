# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.
> The four loops below are the M2 starting point - adapt if your product has 2 or 6 loops instead of 4.

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | 2/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | 2/5 |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | 3/5 |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | 1/5 |

### Correction Loop - 2/5
**What you capture today:**
Users can accept, edit, dismiss, or override AIM Intelligence recommendations. For example, an A/R user may change an account priority, modify the recommended action, edit an outreach message, or reject a recommendation entirely. In the initial prototype, these actions can be captured, but they are not yet automatically used to improve future recommendations.
**How it compounds:**
Over time, AIM can connect each recommendation to the user's correction and the eventual business outcome. This creates a dataset showing where AIM was right, where users disagreed, and which decisions produced better cash-flow and throughput results. Those signals can be used to improve ranking logic, recommendations, and model evaluation.
### Preference Loop - 2/5
**What you capture today:**
AIM can potentially capture how users respond to recommendations—for example, whether they usually accept, modify, postpone, or reject suggested actions. It may also capture business-specific rules such as when customers are contacted, how aggressively collections are handled, and how different types of throughput decisions are prioritized. Persistent personalization is not yet built.
**How it compounds:**
As AIM learns how a specific company operates, recommendations can become more tailored to that business rather than relying on generic rules. For example, AIM may learn that a company prefers to wait 15 days before contacting long-term customers or that certain constraint resources should receive greater weight when prioritizing work.

### Domain Context Loop - 3/5
**What you capture today:**
AIM has the potential to connect data across accounting and operations, including receivables, sales orders, inventory, purchasing, work orders, production constraints, Totally Variable Cost, and throughput.
A receivables decision therefore does not have to be evaluated in isolation. AIM can consider whether an overdue customer also has open orders, whether those orders require constrained capacity, and how much future throughput is associated with them.
**How it compounds:**
Activity in one AIM module improves intelligence in another.
For example:
Receivables → Sales Orders → Production → Constraint → Throughput
A payment issue can influence a sales-order decision, which can influence production scheduling and ultimately throughput. As AIM captures more of these relationships, its recommendations can become increasingly cross-functional and harder for a standalone accounting AI tool to reproduce.
### Network Loop - 1/5
**What you capture today:**
AIM customers currently operate primarily as independent datasets. One customer's use of AIM Intelligence does not meaningfully improve the product for another customer.
**How it compounds:**
With appropriate privacy controls and customer consent, AIM could eventually learn from anonymized and aggregated outcome patterns across customers without exposing individual company data.
For example, AIM could identify patterns such as:
Which collection actions tend to produce faster payment
Which inventory conditions commonly precede throughput loss
Which constraint-utilization patterns correlate with declining throughput
How similar manufacturers respond to specific operational conditions
This could eventually create industry-level benchmarks and improve recommendations for new customers more quickly.

**Total Flywheel Score: 8/20**

**Weakest Loop:** 1/5 Network

**Fix for weakest loop:**
Build an opt-in, privacy-preserving learning layer that uses aggregated recommendation and outcome data across customers to identify benchmark patterns and improve AIM Intelligence without exposing individual customer information.
---

## Encroachment Threat Assessment

### 1. Platform Encroachment
**Attacker:**Intuit / QuickBooks
**Vector:** 
Adds broader AI decision intelligence across receivables, cash flow, payments, reporting, and business operations using the financial data it already owns. It could replicate basic prioritization, recommendations, alerts, and AI-generated actions quickly.
**Time-to-threat:** 6-12 months
**% of value at risk:** 60%

### 2. Vertical Competitor
**Attacker:** AccountingSuite 
**Vector:**
Extends its existing accounting, inventory, sales, purchasing, and operational workflows with AI that surfaces issues and recommends actions across the business. Because its product footprint is closer to AIM, it could mimic much of the cross-functional intelligence experience.
**Time-to-threat:** 6-12 months
**% of value at risk:** 75%

### 3. Adjacent Expansion
**Attacker:** Oracle NetSuite
**Vector:**
Expands AI-driven ERP intelligence further down-market, combining financial, customer, inventory, order, and manufacturing data to recommend operational and financial actions.
**Time-to-threat:** 12-24 months
**% of value at risk:** 50%

---

## 90-Day Encroachment Plan

*Your partner played the Big Tech attacker. What was their plan to kill you?*

**Attacker:** Intuit/Quickbooks
**Attack vector (target the weakest loop):**
Use QuickBooks’ large customer base and existing accounting data to create cross-customer benchmarks and AI recommendations that improve faster as more businesses use them. Bundle the capability into the existing QuickBooks experience so customers receive useful intelligence without adopting a separate product.
**Weeks 1-4 - what they ship:**
Launch a “Business Priorities” experience inside QuickBooks that identifies what needs attention across receivables, cash flow, expenses, and customer activity. It prioritizes issues, explains why they matter, predicts potential impact, and recommends next actions. Because QuickBooks already has large volumes of transaction and payment data, it can also introduce peer benchmarks such as typical payment behavior and cash-flow patterns for similar businesses.
**Weeks 5-8 - how they poach users:**
Bundle the intelligence into an existing QuickBooks plan or offer it as a low-cost upgrade. Target small businesses with messaging such as “Know what needs attention before it becomes a problem.” Use existing accountant relationships, customer channels, and easy data migration to reduce the friction of trying or switching to the new capability.
**Weeks 9-12 - why users don't come back:**
Once customers begin using the intelligence inside the same system where they invoice, receive payments, reconcile accounts, and work with their accountant, switching becomes less attractive. QuickBooks also begins learning each company’s behavior and accumulating recommendation and outcome history, increasing personalization over time.
**Your defense:**
Deep integration across accounting, sales, inventory, purchasing, work orders, production, and constraints.
Proprietary Throughput Accounting decision logic.
Capturing every accept, edit, rejection, and override of an AI recommendation.
Connecting those decisions to actual throughput and financial outcomes.
Building customer-specific intelligence that learns how each business operates.
Creating privacy-safe benchmarking where appropriate.
Making AIM's recommendations explain constraint and throughput impact, not merely financial risk.
