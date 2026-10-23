---
description: >-
  HFT Market Making is a high-frequency market-making strategy on Binance ETH
  perpetual futures, curated by AdverseGuard Alpha. USDC deposits on Solana with
  weekly redemptions.
---

# HFT Market Making

## Overview

HFT Market Making is a high-frequency market-making strategy on ETH USDⓈ-M perpetual futures on Binance. It reads the order book in real time and updates its buy and sell quotes many times a second, instead of holding a view for minutes or hours.

Order-flow signals (who is buying, who is selling, and how the queue changes) let it quote closer to the live price, and step aside when the market is about to move against it. Speed is the edge: it can provide liquidity when slower participants cannot, capture small spreads many times over, and keep inventory small so that a single price swing does not become a large position.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies">https://www.neutral.trade/strategies</a></td></tr></tbody></table>

## Key Facts

| Item                | Detail                                   |
| ------------------- | ---------------------------------------- |
| **Category**        | Market Neutral                           |
| **Curator**         | AdverseGuard Alpha                       |
| **Instrument**      | ETH USDⓈ-M perpetual futures (ETHUSDT)   |
| **Venue**           | Binance, market maker program tier MM1   |
| **Deposit asset**   | USDC on Solana                           |
| **Management fee**  | 1% per year                              |
| **Performance fee** | 50% of profit above your high-water mark |
| **Withdrawal fee**  | 0.3%                                     |
| **Redemptions**     | Once weekly, on Friday                   |

The vault's Details view in the app shows the current terms, including the minimum deposit. See [Fees + Redemption Period](../../../additional-info/fees-+-redemption-period.md).

## How It Works

**Order-book signals.** The system watches the Binance ETHUSDT order book tick by tick. Short-horizon signals from order flow and queue changes estimate where the price is about to go in the next moments.

**Quoting.** The strategy places bids and asks around that short-term fair price, not around the current mid-price. It re-prices its quotes many times a second as the book changes.

**Stepping aside.** When the signals show that a fast move is starting against its quotes, the strategy pulls or widens them. This reduces adverse selection: being filled just before the price moves the wrong way.

**Inventory control.** Positions are kept small and turned over quickly, so the strategy earns from many small trades instead of from holding a market view.

#### Venues

**Centralized:** Binance. The strategy trades on Binance's market maker program at tier MM1, which pays a rebate on maker fills.

### Yield Sources

* Bid-ask spread capture
* Maker rebates (Binance MM1 tier)
* Short-term order-flow and queue signals

## Track Record

The figures below are firm-reported for the strategy's first 61 days of trading, 1 August to 1 October 2026. They come from AdverseGuard Alpha's own record, before the strategy was available on Neutral Trade. They are not vault results.

| Metric                | Strategy |
| --------------------- | -------- |
| Cumulative return     | 41.97%   |
| Sharpe ratio          | 8.18     |
| Sortino ratio         | 22.89    |
| Max drawdown          | -2.46%   |
| Annualized volatility | 30.71%   |
| Best day              | 6.55%    |
| Worst day             | -3.00%   |

## Risk Management

**Trading system controls.** Risk limits run inside the trading application. They monitor position size and exposure in real time and cut quoting or reduce positions when limits are reached.

**Adverse-selection detection.** The same signals that set quotes also detect fast directional moves. When they trigger, quoting is scaled back or paused until conditions normalise.

**Small inventory.** The strategy aims to hold small positions for short periods, which limits how much a single price swing can cost.

## Custody & Security

Depositor capital never leaves institutional custody. Funds are mirrored into a dedicated execution-only sub-account that the curator trades, but cannot withdraw to any external address.

| Layer            | Detail                                                                      |
| ---------------- | --------------------------------------------------------------------------- |
| Custody          | Ceffu (MirrorX) — Binance                                                   |
| Execution venue  | Binance                                                                     |
| Vault accounting | Fully on-chain: NAV, share mint/burn, high-water marks, fee accrual         |
| Blockchain       | Solana                                                                      |
| Vault program    | NT Bundle V1, audited by Halborn, Quantstamp, Offside Labs, and Adevar Labs |

Full details: [Security](../../../neutral-strategy-vaults/security.md).

## Risk Factors

* **Inventory risk.** The strategy aims to stay close to flat, but it holds short-lived ETH positions between fills. A sharp, fast ETH move can cause a loss before the position is closed.
* **Speed and infrastructure risk.** The edge depends on low latency and system uptime. Outages, exchange incidents, or faster competitors can reduce or reverse returns.
* **Fee-tier dependency.** Returns include maker rebates from the Binance MM1 tier. A change to the tier or to Binance's fee schedule changes the return.
* **Single instrument and venue.** All trading is in one contract (ETHUSDT) on one venue (Binance).
* **No guarantee of returns.** Past drawdown levels do not limit future losses.

The [Risk Overview](../../risk-overview/) covers these risks in more detail.

## Why AdverseGuard Alpha?

AdverseGuard Alpha operates at the intersection of traditional finance and digital assets, deploying a multi-strategy quantitative framework across global markets. It also curates [Mid-frequency Market Making](mid-frequency-market-making.md) and [CTA - Momentum LongShort](../directional/cta-momentum-longshort.md) on Neutral Trade.

The team has deep roots in high-frequency trading, asset management, and exchange infrastructure, with decades of combined institutional experience from firms including Tower Research, Citadel, Susquehanna (SIG), Kronos Research, Point72, State Street, RBC, and J.P. Morgan.

{% hint style="info" %}
AdverseGuard Alpha is an alias. We've excluded the curator's full name to mitigate alpha leaking. Neutral Trade has completed thorough due diligence on the team and its strategy.
{% endhint %}

_Products referenced are not intended for individuals in the United States, Mainland China, Hong Kong, sanctioned, or other restricted jurisdictions. This page is for informational purposes only and does not constitute an offer, solicitation, or recommendation to buy or sell any financial instrument. Digital-asset strategies involve significant risk, including possible loss of principal. See the_ [_Risk Warnings and Disclaimers Statement_](../../../legal/risk-warnings-and-disclaimers-statement.md)_._
