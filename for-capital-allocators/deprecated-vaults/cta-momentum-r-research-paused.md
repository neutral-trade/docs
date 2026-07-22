# CTA-Momentum (R\* Research) \[Closed]

{% hint style="danger" %}
**⚠️ Deprecated vault — historical reference only.**

This vault has been deprecated and is no longer active on Neutral Trade. It is not accepting deposits and is not part of the current product line-up. Do not present this strategy as available or current. For live vaults and current data, see the active strategies and the API reference at https://www.neutral.trade/api/v1/docs.
{% endhint %}

#### Disclaimer (R\* Research)

{% hint style="info" %}
We’ve excluded R\* Research’s full name to mitigate alpha leaking. Neutral Trade has already completed thorough due diligence, including eight solid months of live, real-money testing.
{% endhint %}

## Overview

The **CTA-Momentum Strategy** is a multi-asset, machine learning-driven trading strategy operated by Neutral Trade in collaboration with R\* Research. It is designed to capture **short-term momentum and mean-reversion inefficiencies** in highly liquid digital assets.

The strategy is executed on two of the most liquid centralized exchanges globally, providing the lowest available trading fees and superior execution quality. It is structured with robust institutional-grade risk controls and custody and settlement architecture, enabled by our strategic partnerships.

R\* Research CTA-Momentum embodies Neutral Trade’s mission to bring **hedge-fund-quality strategies** to on-chain users.

## Strategy Design

CTA-Momentum's objective is to generate consistent, risk-adjusted returns by identifying short-term mispricings across highly liquid digital assets. It aims to deliver uncorrelated alpha that is resilient across varying market regimes.

#### Alpha Source

* **Momentum + Mean Reversion** patterns in L2 order book data and price action
* **High-Frequency Signal Generation** (every minute)
* **Alternative Data** for sentiment and behavioral insight

#### Asset Coverage

* BTC
* ETH
* SOL
* BNB
* XRP
* DOGE

#### Frequency & Turnover

* **Median Holding Period:** \~1–3 hours
* **Trades:** 3-5 per asset per day
* **Monthly Turnover:** Up to 1000x TVL

#### Risk Controls

* **Target Volatility:** 15%
* **Dynamic Position Sizing:** If risk thresholds are breached, positions are reduced by 50%
* **Drawdown Protection Cap:** 20%
  * Full strategy pause and reevaluation if a drawdown exceeds 20%
* **Max** **Historical Drawdown:** 15%

### Custodial Infrastructure

#### Copper/CEFFU Custody & ClearLoop/MirrorX Settlement

* Assets remain in Copper and CEFFU cold wallets
* Reduced counterparty risk - PnL and margin are net settled to OKX and Binance via ClearLoop & MirrorX
* Protected by English Law trust structure
* 2-of-3 MPC security infrastructure (ensuring funds are never exposed to a single private key being compromised)

### Execution

#### OKX & Binance

* Market Maker Tier Accounts (VIP 7 for OKX and MM-1 for Binance)
  * Institutional-grade liquidity and speed
  * Minimal fees
* Strategy executes via an externally managed Neutral Trade account
  * Protects trader alpha

### Why R\* Research?

* **Extensive Hedge Fund Experience**
* **Proprietary ML Engine** tuned for real-time crypto markets
* **Diversification:** Adds uncorrelated alpha to Neutral Trade's strategy mix
* **On-Chain Transparency** and operational alignment with Neutral Trade

### Historical Performance

#### Backtest Results (1x leverage, 2bps fees)

| Asset | Sharpe | APR  | Max DD | Median Holding |
| ----- | ------ | ---- | ------ | -------------- |
| BTC   | 3.5    | 150% | 10%    | 2 hours        |
| ETH   | 3.5    | 200% | 12%    | 3 hours        |
| SOL   | 4.0    | 300% | 15%    | 1 hour         |

#### **Live Trading on OKX**

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

### Monthly OKX & Binance Reports

{% hint style="info" %}
[https://drive.google.com/drive/folders/19NykpcRylT41y3GDnfxrewCfO7D52-mn?usp=drive\_link](https://drive.google.com/drive/folders/19NykpcRylT41y3GDnfxrewCfO7D52-mn?usp=drive_link)
{% endhint %}

***

CTA-Momentum (R-Research). Launch Date - 4 July 2025
