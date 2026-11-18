---
description: >-
  A market-neutral, mid-frequency market making strategy curated by AdverseGuard
  Alpha, on crypto and TradFi perpetuals. USDC deposits on Solana with weekly
  redemptions.
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

# Mid-frequency Market Making

## Overview <a href="#docs-internal-guid-bcd172ee-7fff-eec8-8ec6-59bba23b723f" id="docs-internal-guid-bcd172ee-7fff-eec8-8ec6-59bba23b723f"></a>

This is a mid-frequency market-making strategy designed to generate steady returns by providing liquidity to Binance Perpetual Futures markets. It runs two maker books in one vault:

* **Core book (crypto perpetuals).** It continuously adjusts its quote pricing and activity based on current conditions. The excess return stems from both the predictive power of a proprietary fair price model, as well as high-quality trade execution capability.
* **TradFi pairs book.** It trades high-volume equity and other traditional-market tickers that are listed as perpetuals on Binance. A mid-term signal decides when to enter, cool down and exit. The book takes a small edge, then steps out.

When risk increases, both books scale back to protect capital.

{% hint style="info" %}
**Strategy upgrade:** AdverseGuard Alpha has added the TradFi pairs book to this strategy. TradFi pairs give the strategy a second source of maker returns, from markets that move on different drivers than crypto.
{% endhint %}

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies/adverseguard-alpha">https://www.neutral.trade/strategies/adverseguard-alpha</a></td></tr></tbody></table>

_Live since April 23, 2026_

## How it works <a href="#docs-internal-guid-6a3917eb-7fff-4b82-1ba4-a43521243508" id="docs-internal-guid-6a3917eb-7fff-4b82-1ba4-a43521243508"></a>

### Core book: crypto perpetuals

**Spread capture** — The system continuously quotes both sides of the ETHUSDT perpetual futures order book on Binance. By maintaining active bid and ask quotes, it earns the spread between buy and sell prices and collects maker rebates.

**Fair price model** — At the core of the strategy is a proprietary model that estimates the true fair price of ETHUSDT in real time. By positioning quotes relative to this fair price rather than the midpoint of the current spread, the strategy improves the profitability of each filled trade.

**Adverse selection detection** — A second predictive model monitors for signs of large incoming directional moves and detects adverse selection, the risk of being on the wrong side of a significant price shift. When these signals trigger, quoting activity is automatically scaled back or paused until conditions normalise.

The result is an asymmetric return profile: consistent spread income in stable conditions, with automated pullback when conditions deteriorate.

### TradFi pairs book

**Universe** — The book trades high-volume TradFi tickers, such as equities, that are listed as perpetual futures on Binance.

**Signal-led entry and exit** — A live mid-term markout signal decides when to enter, cool down and exit. When the signal shows that the mid price is off, the book posts maker liquidity, takes a small edge (about 10 to 20 basis points), then steps out.

**Flat by default** — When the signal is weak or missing, the book holds no position.

**Session rules** — The book follows US equity session rules.

#### Venues

**Centralized:** Binance

### Yield Sources

* Bid-Ask spreads
* Maker rebate
* Short-term market inefficiencies
* Short-term mispricing on TradFi pairs

<figure><img src="../../../.gitbook/assets/cumulative_return_1_5x_realized.png" alt=""><figcaption><p>Core book (crypto perpetuals)</p></figcaption></figure>

## Risk Management

The strategy employs a stop-loss framework designed to catch risk at both the execution and portfolio level.

**Trading System Controls** The first layer operates directly within the trading application. It monitors real-time position exposure and triggers automated stop-loss actions at the strategy level, responding to adverse price moves before losses compound.

**Drawdown Profile** The maximum observed drawdown was -5.42%, recorded on October 10 of last year. The strategy has not breached this level since.

**TradFi Book Limits** The TradFi pairs book keeps leverage low (about 2x) and has a 10% hard stop. Position caps and cool-downs keep its risk tight.

**Dynamic Risk Scaling** Beyond stop-loss controls, the strategy's predictive model continuously monitors for adverse selection and directional risk. When risk conditions elevate, quoting activity is automatically scaled back or paused, prioritizing capital preservation over incremental spread capture.

## Why AdverseGuard Alpha?

AdverseGuard Alpha operates at the intersection of traditional finance and digital assets, deploying a multi-strategy quantitative framework across global markets.

Their edge is built on a world-class team with deep roots in high-frequency trading, asset management, and exchange infrastructure. They bring decades of combined institutional experience from industry titans including Tower Research, Citadel, Susquehanna (SIG), Kronos Research, Point72, State Street, RBC, and J.P. Morgan. This institutional pedigree allows them to bridge the gap between legacy financial rigor and the frontiers of digital asset liquidity.

{% hint style="info" %}
We’ve excluded AdverseGuard Alpha’s full name to mitigate alpha leaking. Neutral Trade has completed thorough due diligence, including real-money testing.
{% endhint %}
