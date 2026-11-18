---
description: >-
  A systematic, long-only short-term strategy on Binance perpetual futures,
  curated by RisingCap. Listed on Neutral Marketplace.
hidden: true
noIndex: true
---

# Long Only Systematic Growth

## Overview

Long Only Systematic Growth is a systematic, long-only trading strategy on perpetual futures, curated by RisingCap. It buys short-term upward price impulses in liquid crypto assets and takes profit after small price advances. It is directional, not market-neutral.

The strategy is fully automated and trades often, about 25 to 30 times a day depending on market volatility. Most trades close in under an hour.

Long Only Systematic Growth is listed on [Neutral Marketplace](../). Marketplace strategies passed basic due diligence and have not yet been tested with Neutral Trade capital.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies/solana/6ckTxcr5Lav5QbZjKpD2xm5hfLmx3qPu5qGBWs9Pa58V">https://www.neutral.trade/strategies/solana/6ckTxcr5Lav5QbZjKpD2xm5hfLmx3qPu5qGBWs9Pa58V</a></td></tr></tbody></table>

_Live on Neutral Trade: \[DATE TO BE CONFIRMED]_

_Past performance is not necessarily indicative of future results._

## How it Works

**Identify an impulse.** Completed one-minute price and volume data identify strong short-term advances within an active trading range. The first buy is simulated at the next minute's close.

**Harvest and renew.** A resting take-profit order targets roughly 0.68% above the initial entry. After a profitable exit, elevated activity can permit another entry without a new impulse. Renewal size also responds to the existing quality model.

**Manage adverse inventory.** Predefined lower-price orders add to a losing position and adjust its average entry and profit target. A late-add filter, exposure budgets and age-based exits constrain this process. These controls do not eliminate sustained-downtrend risk.

### Strategy Parameters

| Parameter            | Value                                        |
| -------------------- | -------------------------------------------- |
| Direction            | Long-only (gross and net exposure are equal) |
| Instruments          | USDT perpetual futures                       |
| Markets              | Liquid Binance perpetuals                    |
| Median holding time  | About 21 minutes (average about 3 hours)     |
| Maximum holding time | 14 days                                      |
| Deposits             | Daily                                        |
| Redemption           | Weekly                                       |

### Return Sources

* Short-term price continuation after an impulse
* Repeated profit-taking while markets are active
* Recovery of positions that were added to during price dips

The strategy does not depend on maker rebates or spread capture.

### **Venues**

**Centralized:** Binance, with off-exchange custody through Ceffu (MirrorX)

## Simulated Performance

{% hint style="warning" %}
**These figures are a historical simulation (backtest), not a live track record.** They come from RisingCap and Neutral Trade has not audited them. The simulation includes trading costs of 12.5 bps per round trip. It excludes funding payments, extra slippage, and management and performance fees.
{% endhint %}

Simulation period: 1 July 2024 to 31 October 2026.

| Metric                             | Value  |
| ---------------------------------- | ------ |
| Annualised return (CAGR)           | 33.08% |
| Annualised volatility              | 8.62%  |
| Sharpe ratio (daily, 0% risk-free) | 3.35   |
| Maximum drawdown (daily closes)    | -3.00% |
| Maximum drawdown (minute-level)    | -9.89% |
| Hit rate                           | 99.78% |

A high hit rate does not mean low risk. Adding to losing positions produces many small wins and occasional larger losses.

## Risk Factors

**Directional risk** — The strategy holds only long positions. A sustained market downtrend causes losses.

**Averaging-down risk** — The strategy adds to losing positions. In a long decline, losses can grow larger than the typical gain per trade, and recovery can take a long time.

**Intraday drawdown risk** — Daily closes do not show the full intraday path. In the simulation, the minute-level drawdown was more than three times the daily drawdown.

**Simulation risk** — Results come from a backtest. Live results can differ because of fills, queue position, slippage and funding costs.

**Leverage and liquidation risk** — The strategy uses perpetual futures. Sharp adverse moves can cause losses or forced liquidations.

**Counterparty and exchange risk** — Exposure to venue failure, insolvency or operational disruption. Mitigation: off-exchange custody and settlement through Ceffu (MirrorX).

**Operational risk** — Execution depends on trading infrastructure, exchange APIs and custody integrations being available.

### Risk Management

| Control              | Rule                                                                                     |
| -------------------- | ---------------------------------------------------------------------------------------- |
| First entry          | 0.60% of NAV                                                                             |
| Per-token add budget | 15% of NAV                                                                               |
| Portfolio add budget | 75% of NAV                                                                               |
| Concurrent positions | Up to 7 tokens, up to 8 buys per position                                                |
| Loss reduction       | 33% cut after 36 hours if the loss is beyond 750 log-bps; full exit beyond 1,000 log-bps |
| Time-based exit      | Exit review after 7 days for a loss beyond about 4.88%; 14-day maximum hold              |

These budgets apply to new orders. They are not hard limits on exposure after prices move. The strategy has no portfolio-wide hard drawdown stop.

## Custody & Security

Ceffu (MirrorX) is used for institutional off-exchange custody and settlement.

On-chain vault infrastructure, covering deposits, withdrawals and on-chain operations, operates under the Neutral Strategy Vaults standard multi-party approval framework, independent of the centralised exchange custody arrangements. Full details: [Security](../../../neutral-strategy-vaults/security.md).

## Why RisingCap?

[RisingCap](https://risingcap.co/liquid-fund/) is a systematic quantitative firm that builds risk-controlled strategies across liquid markets. The firm traded only its own capital for an extended period to test its infrastructure and risk management before it opened strategies to outside capital.

The trading team is based in Dubai (GST, UTC+4) and India (IST, UTC+5:30). Automated systems monitor the strategy 24/7.

To do your own due diligence on the team, visit [risingcap.co/liquid-fund](https://risingcap.co/liquid-fund/).
