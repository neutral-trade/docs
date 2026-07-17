# Delta Neutral Arbitrage

## Overview

Delta Neutral Arbitrage is a market-neutral strategy arbitrage vault curated by Velox Trading Group. The strategy seeks to maximize absolute returns while mitigating downside expressed in broader crypto markets. To meet this objective the strategy deploys capital across four arbitrage pillars: low-latency exchange arbitrage, funding and basis arbitrage, DeFi-centric market making.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies/velox-cross-usdc-bundle">https://www.neutral.trade/strategies/velox-cross-usdc-bundle</a></td></tr></tbody></table>

_Live on Neutral Trade: 2026-06-09_

_Past performance is not indicative of future results._

## How it works

The strategy operates four complementary arbitrage pillars concurrently.

* **Low-latency exchange arbitrage**
* **Funding and basis arbitrage**
* **DeFi-centric market making**

The portfolio targets a cash leverage rate of 1.5x in addition to the on exchange and derivative leverage. This is a long term target using leverage from prime brokers to enhance the overall return profile.

#### Venues

**Centralized:** Binance, OKX, Bybit, Gate

**Decentralized:** Hyperliquid, Lighter

For a subsequent phase:

* KuCoin

### Yield Sources

* Cross-venue pricing inefficiencies captured through simultaneous offsetting trades
* Funding rate and basis spreads captured through delta-neutral positioning
* Short-term dislocations around market events

## Risk Factors

**Counterparty and exchange risk** — Trading across exchanges creates exposure to venue-level failure, insolvency, or operational disruption. Mitigations include:  off-exchange custody and settlement via Copper (ClearLoop) and Ceffu (MirrorX) for centralised exchange trading, and diversification across six venues at launch with additional venues planned.

**Liquidation and ADL risk** — The strategy operates at 1.5x leverage. Sharp price moves or correlated venue stress can trigger forced liquidation or Auto-Deleveraging on perpetual futures positions. Mitigations include: a conservative leverage profile relative to typical arbitrage strategies, continuous position monitoring, and trading in liquid markets where rebalancing is reliable.

**Execution and market microstructure risk** — Market making and short-horizon strategies are sensitive to execution quality. Adverse selection, being filled on the wrong side of a directional move, can erode spread income.

**Smart contract risk** — DeFi-centric market making involves interaction with on-chain protocols and inherits the smart contract risk of those venues. This risk cannot be eliminated entirely.

**Operational risk** — Multi-venue, multi-strategy execution depends on the continuous availability of trading infrastructure, exchange APIs, and custody integrations. Disruption at any layer can prevent timely rebalancing.

## Custody & Security

For positions on centralised exchanges, we use Copper (ClearLoop) and Ceffu (MirrorX), institutional off-exchange settlement providers, reducing exposure to exchange-level insolvency.

On-chain vault infrastructure, covering deposits, withdrawals, and on-chain operations, operates under Neutral Strategy Vaults standard multi-party approval framework, independent of the centralised exchange custody arrangements. Full details: [Security](https://docs.neutral.trade/vault-infrastructure/security).

## Why Velox Trading Group?

[Velox Trading Group](https://www.veloxtrading.ai/) is a digital asset quantitative investment and technology firm. The team comprises traders, engineers, mathematicians, and data scientists with specialisation in crypto market microstructure across both centralised and decentralised venues.
