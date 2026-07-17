---
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Curator Selection

Neutral Trade only lists strategies run by trading teams that pass a standardized vetting framework. Every prospective curator is assessed across **six weighted dimensions**, scored on a common scale, and reviewed against a fixed decision matrix. The framework is designed to prioritize the factors most critical to risk management and yield quality for depositors.

{% hint style="info" %}
**What this means for depositors:** every vault on Neutral Trade is backed by a trading team that has passed verified track-record checks, risk-control review, and operational due diligence — not just a pitch deck.
{% endhint %}

### Scoring Methodology

Each dimension is scored 1–5 and combined into a weighted average:

| Rating       | Score | Description                                   |
| ------------ | ----- | --------------------------------------------- |
| Excellent    | 5     | Exceeds requirements, institutional-grade     |
| Strong       | 4     | Meets all requirements with notable strengths |
| Acceptable   | 3     | Meets minimum requirements                    |
| Marginal     | 2     | Below requirements, requires remediation      |
| Unacceptable | 1     | Fails to meet standards                       |

**Minimum passing score: 3.5 / 5.0 (70% weighted average).** Teams below this threshold are not onboarded.

### The Six Evaluation Dimensions

#### 1. Strategy & Track Record — 25%

The most heavily weighted dimension, together with risk management.

* **Live trading duration** — 3+ years of live trading scores highest; under 6 months fails. Backtests alone are never sufficient.
* **Performance quality** — annualized return, Sharpe ratio (1.5+ expected; 2.0+ strong), max drawdown (under 15% preferred), win rate, and month-to-month return consistency.
* **Strategy clarity** — a clearly articulated edge, an appropriate asset universe, and a fully systematic execution model. Manual components require explicit justification.

**Verification is mandatory, not optional.** We require daily PnL with timestamps and historical trade logs, and for larger allocations, read-only exchange API access. Third-party audited returns are strongly preferred. Self-reported spreadsheets are not accepted as sole evidence.

> Strategies with an exceptional decorrelation profile against our existing vault line-up may qualify with a lower Sharpe ratio than the standard threshold.

#### 2. Risk Management — 25%

* **Exposure controls** — defined gross exposure limits (leverage up to 3–4× is acceptable with a clear rationale; undefined limits fail), a stated net exposure range consistent with any market-neutral claim, and single-asset concentration limits (below 30% preferred).
* **Drawdown management** — hard daily loss limits, weekly escalation thresholds, documented de-risking procedures, and clear re-entry criteria after a drawdown.
* **Operational risk** — system redundancy and failover, multi-venue execution to reduce counterparty risk, manual override capability for automated systems, and a clean (or transparently explained) incident history.

#### 3. Infrastructure & Technology — 15%

* **Execution** — proprietary execution infrastructure scores highest; latency and order-type support must match the strategy type; slippage management must be documented.
* **Research process** — quality of data sources, systematic strategy development, backtesting rigor (out-of-sample testing, regime analysis), and a sensible model-update cadence.
* **Security** — withdrawal-disabled API keys with IP whitelisting, version-controlled code with access controls, and complete audit trails.

#### 4. Operational Maturity — 15%

* **Team** — depth beyond a single key person, relevant quant/crypto experience, clear roles, and continuity provisions. Single-operator teams face heightened key-person-risk scrutiny.
* **AUM & capacity** — meaningful existing AUM, a realistic stated capacity for the strategy, and room to absorb a Neutral Trade allocation without performance degradation.
* **Reporting** — daily reporting preferred (weekly minimum), standardized formats, responsive communication, and willingness to provide read-only API visibility in real time.

#### 5. Counterparty & Legal — 10%

* Appropriate legal entity structure and jurisdiction, regulatory status, and operational history.
* Documentation review: entity formation documents, beneficial ownership disclosure, AML/KYC policies, and insurance coverage.
* Reference checks with existing investors, exchange relationships, and service providers.

#### 6. Alignment & Fit — 10%

* **Portfolio fit** — diversification benefit to the existing vault line-up, low correlation to current allocations, and limited asset overlap. We often prefer a genuinely uncorrelated niche strategy over a higher-capacity strategy that overlaps with existing vaults.
* **Commercial terms** — competitive fees, acceptable liquidity and redemption terms, and willingness to meet our transparency standards.
* **Partnership potential** — sustainable business model, aligned growth incentives, and responsive communication.

### Decision Matrix

| Weighted Score | Outcome            | What Happens                                                |
| -------------- | ------------------ | ----------------------------------------------------------- |
| 4.5 – 5.0      | **Strong approve** | Fast-track onboarding; larger initial allocation considered |
| 3.5 – 4.4      | **Approve**        | Standard onboarding with identified remediation items       |
| 3.0 – 3.4      | **Conditional**    | Significant remediation required before any allocation      |
| 2.0 – 2.9      | **Decline**        | Material deficiencies; may reapply in 6–12 months           |
| Below 2.0      | **Hard decline**   | Fundamental incompatibility                                 |

### Automatic Red Flags

The following findings trigger immediate escalation and will block onboarding regardless of the overall score:

* Inability to verify the track record
* History of significant operational failures
* Undisclosed material risks
* Regulatory issues or sanctions exposure
* Refusal to provide standard documentation
* Inconsistencies in reported data
* Key-person departure during due diligence
* Adverse reference checks

### Due Diligence Questionnaire

Every prospective team completes a standardized DDQ covering six areas: strategy overview and edge, historical performance data, the risk framework and incident history, operations (team, infrastructure, security), legal and compliance, and commercial terms. The DDQ responses feed directly into the dimension scores above.
