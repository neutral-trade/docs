---
description: >-
  A systematic, market-neutral funding-rate arbitrage strategy curated by CWM.
  Trades Binance, Gate and KuCoin with off-exchange custody. Listed on Neutral
  Marketplace.
---

# Hachiko

## Overview

Hachiko is a systematic, market-neutral strategy that earns funding payments in crypto perpetual futures markets. It is curated by [CWM](https://www.cwmtrading.com/). The strategy holds a perpetual futures position and an offsetting hedge in the same instrument. The hedge removes the exposure to market direction, so the strategy keeps the net funding income.

Proprietary quantitative models and automated execution make the trade selection, position sizing, entry and exit, and hedge adjustments.

Hachiko is listed on [Neutral Marketplace](../). Marketplace strategies passed basic due diligence and have not yet been tested with Neutral Trade capital.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies/solana/7974f3xGs6utPBfZgwCAB4EZyajbERyogHwdyZLqD71C">https://www.neutral.trade/strategies/solana/7974f3xGs6utPBfZgwCAB4EZyajbERyogHwdyZLqD71C</a></td></tr></tbody></table>

_Live on Neutral Trade: 18 Nov 2026_

_Past performance is not necessarily indicative of future results._

## How it Works

**Identify** — The models scan perpetual futures across the supported exchanges for favorable funding rates. They forecast short-term funding behavior and select only the trades where expected funding is larger than execution fees, hedging costs and basis changes.

**Hedge** — Each funding position is paired with an offsetting position in the same instrument. The portfolio is built to stay market neutral.

**Execute** — An in-house, low-latency C++ trading engine opens and closes the positions. The engine can also capture small price differences while it builds each position.

**Monitor and adjust** — The system tracks margin levels, liquidation distance and market data 24/7. When funding conditions change, the models enter or exit positions and rebalance across exchanges.

### Strategy Parameters

| Parameter        | Value                                            |
| ---------------- | ------------------------------------------------ |
| Strategy type    | Market neutral: funding-rate arbitrage           |
| Instruments      | Perpetual futures, hedged in the same instrument |
| Account leverage | About 2x (maximum 3.5x)                          |
| Deposits         | Daily                                            |
| Redemptions      | Weekly                                           |

### Yield Sources

* Funding payments on perpetual futures
* Small price differences captured while building positions

### **Venues**

**Centralized:** Binance, Gate and KuCoin at launch.

## Performance

The figures below come from CWM's live trading record. Neutral Trade has not audited them. They are shown before Neutral Trade fees.

Record period: 13 May 2025 to 31 October 2026.

| Metric                   | Value    |
| ------------------------ | -------- |
| Cumulative return        | 37.38%   |
| Annualised return (CAGR) | 24.14%   |
| Annualised volatility    | 1.47%    |
| Maximum drawdown (daily) | -1.26%   |
| Negative days            | 2 of 536 |

In this period, funding payments made all of the profit. Trading results from entering, exiting and hedging positions were a small net cost.

#### Monthly Returns

| Year | Jan    | Feb   | Mar   | Apr   | May   | Jun   | Jul   | Aug   | Sep   | Oct   | Nov   | Dec   |
| ---- | ------ | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 2025 | –      | –     | –     | –     | 0.65% | 0.92% | 2.16% | 1.11% | 2.51% | 2.37% | 2.20% | 1.35% |
| 2026 | -0.09% | 0.63% | 0.98% | 2.53% | 3.20% | 1.93% | 2.20% | 2.83% | 2.73% | 1.90% | –     | –     |

May 2025 is a partial month (from 13 May).

## Risk Factors

**Funding reversal** — Funding rates can fall, turn negative and stay negative. The strategy then earns less, or pays instead of receives. Returns depend on the level of funding in the market.

**Leverage and liquidation risk** — The strategy uses about 2x account leverage. A sharp price move can trigger liquidation or auto-deleveraging of one leg before the other leg can be adjusted.

**Counterparty and exchange risk** — Exposure to venue failure, insolvency or operational disruption. Mitigation: off-exchange custody and settlement (see below).

**Operational risk** — Execution depends on trading infrastructure, exchange APIs and custody integrations being available.

### Risk Management

* **Liquidation distance** — Positions keep a liquidation price at least 2x away from the market price.
* **Leverage cap** — Account leverage is capped at 3.5x.
* **Liquidity filter** — The models select only pairs with enough liquidity and volume.
* **Pre-trade checks** — Automated pre-trade checks and risk alerts run on every order.
* **24/7 monitoring** — An in-house portfolio management system tracks PnL, positions and leverage around the clock.

## Custody & Security

The strategy trades in Neutral Trade sub-accounts through a trade-only API. The curator cannot withdraw funds.

* **Binance and KuCoin:** off-exchange custody and settlement through Ceffu (MirrorX).
* **Gate:** off-exchange custody and settlement through Copper (ClearLoop).

On-chain vault infrastructure, covering deposits, withdrawals and on-chain operations, operates under the Neutral Strategy Vaults standard multi-party approval framework, independent of the centralised exchange custody arrangements. Full details: [Security](../../../neutral-strategy-vaults/security.md).

## Why CWM?

CWM is a team of high-frequency trading engineers and researchers with backgrounds in traditional finance. The team has run the Hachiko strategy since May 2025. Website: [cwmtrading.com](https://www.cwmtrading.com/).

* **Research and investor relations** are co-led by a founder with more than 17 years in high-frequency trading. He worked on the interest rates systematic market making desk at Goldman Sachs in New York, and earlier as a senior developer at Tower Research Capital.
* **Trading infrastructure and daily operations** are led by a co-founder who built ultra-low-latency C++ trading systems. He was a tech lead at Kronos Research and worked at Point72, JP Morgan and RBC in New York.
* **Operations and compliance** are led by a head of business development who manages back office, compliance and investor relations.

The trading team covers operations 24/7 (UTC+8).
