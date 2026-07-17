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

# CTA-Adaptive Alpha

## Overview

CTA-Adaptive Alpha is a fully automated quantitative strategy that extracts short-term alpha from structural inefficiencies in crypto derivatives markets. Unlike the market-neutral vaults on this platform, this strategy is **directional.** It takes long and short positions based on real-time market signals, and returns will correlate to market conditions to some degree.

The strategy adapts dynamically between trend-following and mean-reversion positioning depending on prevailing market conditions, rather than maintaining a fixed directional bias.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies/cta-adaptive-alpha">https://www.neutral.trade/strategies/cta-adaptive-alpha</a></td></tr></tbody></table>

## How it works

The strategy continuously monitors price action and order-flow signals across a universe of liquid crypto derivatives. It identifies short-term mispricings created by volatility expansions, positioning imbalances, and behavioural patterns inherent in leveraged crypto markets.

Positions are taken on both the long and short side, governed by strict price-based and time-based exit rules that enforce disciplined exposure at all times. When signals are weak or market conditions deteriorate, the strategy scales back activity rather than maintaining exposure.

### Alpha Source

* Opportunistic entries during volatility-driven drawdowns (particularly following forced liquidations)
* Short-term trend capture during strong directional continuation phases
* High-Frequency Signal Processing
* Continuous monitoring of price action and order-flow-derived signals
* Behavioural Market Inefficiencies
* Leveraged retail trading behaviour unique to crypto derivatives markets

**Asset universe:** BTC, ETH, XRP, SOL — adjustable based on market conditions

**Activity:** \~6 trades per asset per day, \~20× monthly turnover, 24/7

## Risk Controls

**Daily Maximum Drawdown Target:** \~10%, supported by layered risk constraints designed to limit adverse exposure.\
\
**Systematic Exit Discipline:** All positions are governed by automated price-based and time-based exit rules, ensuring exposure is reduced when predefined risk thresholds are reached.\
\
**Dynamic Risk Allocation:** Capital allocation and strategy weights are adjusted dynamically in response to evolving market conditions, volatility, and signal quality.

**Portfolio-Level Safeguards:** A hard drawdown protection cap of 20% on a daily basis, is enforced at the portfolio level. Upon reaching this threshold, the strategy is paused and subjected to a full risk review and recalibration.\
(This safeguard is intended for extreme scenarios and has not been triggered historically.)

## Why Atlas Research?

A Quantitative team with extensive experience in traditional finance, including multi-year backgrounds as fund managers, analysts, and proprietary traders. Deep specialization in crypto-specific market micro-structure. Proven track record of low-drawdown, high-alpha strategies.

\
Conservative philosophy focused on risk first, returns second.

{% hint style="info" %}
We’ve excluded Atlas Research’s full name to mitigate alpha leaking. Neutral Trade has completed thorough due diligence, including real-money testing.
{% endhint %}
