---
hidden: true
icon: light-switch
---

# Copy of Strategy Curator Vetting Framework

This framework provides a streamlined approach to assess prospective strategy curators for Neutral Trade vaults. Curators are evaluated across four key dimensions to ensure alignment with our risk management and yield optimization objectives.

***

### Evaluation Overview

| Rating         | Score | Description                                   |
| -------------- | ----- | --------------------------------------------- |
| Excellent      | 5     | Institutional-grade, exceeds all requirements |
| Strong         | 4     | Meets all requirements with notable strengths |
| Acceptable     | 3     | Meets minimum requirements                    |
| Below Standard | 2     | Requires remediation before approval          |
| Unacceptable   | 1     | Does not meet standards                       |

**Minimum Passing Score:** 3.5 out of 5.0 (weighted average)

***

### Dimension 1: Strategy & Track Record (40%)

#### Performance Requirements

| Metric               | Excellent (5) | Strong (4) | Acceptable (3) | Below (2)  | Unacceptable (1) |
| -------------------- | ------------- | ---------- | -------------- | ---------- | ---------------- |
| Live Trading History | >2 years      | 1-2 years  | 6-12 months    | 3-6 months | <3 months        |
| Annualized Return    | >40%          | 30-40%     | 20-30%         | 10-20%     | <10%             |
| Sharpe Ratio         | >2.5          | 2.0-2.5    | 1.5-2.0        | 1.0-1.5    | <1.0             |
| Max Drawdown         | <10%          | 10-15%     | 15-20%         | 20-30%     | >30%             |

#### Verification Checklist

| Requirement                                                                   | Status |
| ----------------------------------------------------------------------------- | ------ |
| Verified track record (exchange API, third-party audit, or portfolio tracker) | ☐      |
| Historical trade logs with timestamps                                         | ☐      |
| Clear strategy description with defined edge                                  | ☐      |

**Dimension 1 Score:** \_\_\_ / 5.0

***

### Dimension 2: Risk Management (30%)

#### Risk Controls Assessment

| Criteria               | Requirement                                  | Score |
| ---------------------- | -------------------------------------------- | ----- |
| Maximum Leverage       | Clearly defined limits (preferred: ≤3x)      | /5    |
| Daily Loss Limit       | Hard stop defined (e.g., -3% to -5%)         | /5    |
| Drawdown Response      | Documented de-risking procedures             | /5    |
| Position Concentration | Single asset limit defined (preferred: <30%) | /5    |

#### Key Questions

1. What is your maximum leverage policy?
2. What are your hard stop-loss limits (daily/weekly)?
3. How do you respond to drawdown events?
4. Do you have system redundancy and manual override capabilities?

**Dimension 2 Score:** \_\_\_ / 5.0

***

### Dimension 3: Team & Operations (20%)

#### Team Assessment

| Criteria             | Scoring Guidance                                                   | Score |
| -------------------- | ------------------------------------------------------------------ | ----- |
| Relevant Experience  | Background in quantitative trading, crypto, or traditional finance | /5    |
| Team Depth           | Key person risk assessment (single operator vs. team)              | /5    |
| Current AUM          | >$300M (5) / $150-300M (4) / $50-150M (3) / <$50M (2)              | /5    |
| Reporting Capability | Ability to provide live/daily/weekly performance reports           | /5    |

#### Operational Checklist

| Requirement                                 | Status |
| ------------------------------------------- | ------ |
| Clear organizational structure              | ☐      |
| Documented operational procedures           | ☐      |
| Willingness to provide read-only API access | ☐      |

**Dimension 3 Score:** \_\_\_ / 5.0

***

### Dimension 4: Legal & Compliance (10%)

#### Entity & Compliance Check

| Criteria                                      | Status | Notes |
| --------------------------------------------- | ------ | ----- |
| Registered legal entity                       | ☐      |       |
| Jurisdiction disclosed                        | ☐      |       |
| Regulatory status clarified                   | ☐      |       |
| No adverse findings (sanctions, legal issues) | ☐      |       |

**Dimension 4 Score:** \_\_\_ / 5.0

***

### Consolidated Scorecard

| Dimension               | Weight   | Score | Weighted Score |
| ----------------------- | -------- | ----- | -------------- |
| Strategy & Track Record | 40%      | /5.0  |                |
| Risk Management         | 30%      | /5.0  |                |
| Team & Operations       | 20%      | /5.0  |                |
| Legal & Compliance      | 10%      | /5.0  |                |
| **TOTAL**               | **100%** |       | **/5.0**       |

***

### Decision Matrix

| Score     | Decision                     | Action                                            |
| --------- | ---------------------------- | ------------------------------------------------- |
| 4.5 - 5.0 | **Approved**                 | Fast-track onboarding, consider higher allocation |
| 3.5 - 4.4 | **Approved with Conditions** | Standard onboarding, address identified items     |
| 3.0 - 3.4 | **Pending**                  | Requires remediation before final approval        |
| < 3.0     | **Declined**                 | Does not meet minimum standards                   |

***

### Red Flags (Automatic Decline)

Any of the following results in automatic escalation or decline:

* Inability to verify track record
* History of significant losses without explanation
* Refusal to provide standard documentation
* Regulatory issues or sanctions exposure
* Inconsistencies in reported performance data

***

### Onboarding Process (Post-Approval)

#### Week 1-2: Setup

* Execute partnership agreement
* Complete KYC/AML verification
* Establish reporting obligations and communication channels

#### Week 3-4: Integration

* API connectivity setup
* Risk monitoring integration
* Reporting format alignment

#### Week 5-8: Pilot Period

* Initial allocation deployment
* Daily performance monitoring
* Weekly review calls

#### Post-Pilot: Go-Live / Extended Pilot / Withdrawals

* Go-live, extension of the pilot period or withdrawals from the strategy based on pilot performance
* Transition to ongoing monitoring
* Monthly performance reviews

***

_For questions about the vetting process, contact: partnerships@neutral.trade_
