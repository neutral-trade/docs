---
description: >-
  How trading firms and quant teams launch a strategy on Neutral Trade:
  requirements, due diligence, integration, pilot, and full deployment.
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
  anchors:
    visible: true
---

# Curator Onboarding

Neutral Trade invites systematic trading teams to run strategies as **Neutral Strategy Vaults**: you trade, we bring the capital, the infrastructure, and the operations. Strategy IP stays entirely with you.

### Who Should Apply

We look for teams whose strategies meet these baseline requirements:

* **Sharpe ratio of 1.5 or higher** on live performance (exceptions possible for strategies with genuine decorrelation from our existing vaults)
* **Low market bias** — persistently directional strategies are not suitable
* **Fully systematic execution** — no discretionary trading
* **Daily or faster signal frequency**
* **Verifiable live track record** — daily PnL with timestamps and trade logs; backtests alone are not sufficient

We often prefer a genuinely uncorrelated niche strategy over a higher-capacity strategy that overlaps with our existing line-up. The full evaluation criteria, scoring weights, and decision thresholds are on the [Curator Selection](https://docs.neutral.trade/curators/curator-selection) page.

### What You Get

You keep the strategy. We run everything else.

* **One account, many investors** — manage a single account; Neutral Trade aggregates depositor capital and handles per-wallet accounting.
* **Automated fee distribution** — performance fees calculated per wallet with individual high-water marks, paid out automatically.
* **VIP tiers for larger depositors** — set Silver, Gold and Diamond tiers with a performance-fee discount at each, to attract bigger tickets.
* **Your fee tier or ours** — trade in your own sub-account (MSA) at your tier, or in a sub managed account (SMA) at ours.
* **9 venues, already integrated** — Binance, KuCoin, OKX, Bybit, Gate, Bitget, Hyperliquid, Lighter, and a TradFi brokerage, with custody through Ceffu, Copper, and Fordefi MPC.
* **Your IP stays yours** — no code disclosure, no replication commitments, no exclusivity, no non-compete.
* **Full operational support** — investor relations, technical setup, marketing, and a proprietary margin-management system for automated capital rebalancing.

The full stack — venues, custody routes, collateral transfers, daily NAV, and reporting — is described on [Infrastructure for Trading Firms](infrastructure-for-trading-firms.md).

### The Onboarding Process

#### Step 1 — Apply

Fill in the [Google form](https://forms.gle/wKKsqBZmwLkZW4gk8), message the team on [Telegram](https://t.me/neutraltrade), or email [partnerships@neutral.trade](mailto:partnerships@neutral.trade) with a description of your strategy and your track record. You will receive our standardized Due Diligence Questionnaire (DDQ) covering strategy, performance, risk framework, operations, legal, and commercial terms.

#### Step 2 — Due Diligence Review

We score your team against the six-dimension framework described in [Curator Selection](https://docs.neutral.trade/curators/curator-selection). Expect us to ask for daily PnL with timestamps, historical trade logs, and — for larger allocations — read-only exchange API access to verify performance. Reference checks are part of this stage.

#### Step 3 — Legal & Compliance _(weeks 1–2 after approval)_

* Execute NDA
* Complete KYC/AML verification
* Execute the curator agreement, including fee terms
* Agree reporting obligations and cadence

#### Step 4 — Technical Integration _(week 2)_

* API connectivity setup (read-only monitoring access first)
* Alignment on reporting formats
* Integration with Neutral Trade's risk monitoring
* Dedicated communication channel with the NT team
* Training on Neutral Trade's vault tools

#### Step 5 — Pilot Period _(weeks 3–4)_

Your vault launches with an initial allocation under a pilot protocol:

* Daily monitoring against your stated risk limits
* Weekly review calls
* Performance tracked against the expectations set during due diligence

#### Step 6 — Live on Neutral Marketplace _(about 3–4 weeks after terms are agreed)_

After a successful pilot, your vault goes live on Neutral Marketplace and opens to depositors. Monitoring moves to the standard ongoing protocol, with reviews on a quarterly schedule.

#### Step 7 — Neutral Curated _(after 3+ months of good performance)_

Your vault moves to Neutral Curated, our curated line-up, with full marketing support.

To get the most from the platform once you are live, see the nine habits on [Infrastructure for Trading Firms](infrastructure-for-trading-firms.md#get-the-most-from-neutral-trade).

{% hint style="info" %}
**Ongoing expectations:** curators maintain read-only API visibility, meet the agreed reporting cadence (daily preferred), and operate within the risk limits documented during onboarding. Breaches of daily or weekly loss limits trigger the escalation procedures agreed in Step 3.
{% endhint %}

### Get in Touch

Ready to apply? Fill in the [Google form](https://forms.gle/wKKsqBZmwLkZW4gk8), reach out on [Telegram](https://t.me/neutraltrade), or email [partnerships@neutral.trade](mailto:partnerships@neutral.trade) with your track record details — we respond to every serious application.
