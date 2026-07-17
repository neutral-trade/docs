---
hidden: true
---

# HFT Multi-factor

## Overview

The HFT Multi-factor strategy generates market-neutral returns by combining high-frequency trading with market making on major centralized exchanges. The system runs 100+ substrategies built upon machine-learning factor models — multi-factor time-series models that are iteratively refined based on market structure. Alpha is sourced evenly across the two engines: roughly 50% from high-frequency trading signals and 50% from market making.

The strategy focuses on major liquid assets and perpetual futures, validated under market stress conditions, with institutional-scale trading volume supported by in-house execution infrastructure.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies/hft-multi-factor">https://www.neutral.trade/strategies/hft-multi-factor</a></td></tr></tbody></table>

## How it works

**Machine-learning factor framework** — At the core of the strategy is a library of multi-factor time-series models. Signals are researched, deployed, and iteratively refined based on observed market structure, allowing the system to adapt as market regimes shift.

**Diversified alpha signals** — The 100+ substrategies combine market-making, momentum, and mean-reversion dynamics. Diversification across signal families and assets reduces reliance on any single source of return.

**Maker-dominant execution** — Approximately 90% of trade execution is placed as maker orders. The strategy earns bid-ask spread and maker rebates while minimizing taker fees and market impact, supported by high-turnover, institutional-scale execution infrastructure.

**Leverage** — The strategy operates within a 0.7x to 5x leverage range. The Neutral Trade vault mandate runs at 4.5x.

### **Venues**

**Centralized:** Binance

### Yield Sources

* Bid-ask spread capture and maker rebates
* Short-horizon alpha signals (momentum and mean reversion)
* Short-term market inefficiencies

***

## Risk Management

**Quantitative Risk Framework** — A multi-layer risk framework integrates volatility clustering, drawdown limits, correlation stress tests, and scenario simulations to maintain robust performance under varying market conditions.

**Exposure & Monitoring Controls** — Real-time exposure controls are paired with independent monitoring and audit mechanisms to enforce trading constraints, support transparent oversight, and navigate liquidity and volatility shifts.

**Counterparty Risk Management** — Counterparty risk is managed through a structured execution and custody framework across exchanges, on-chain infrastructure, and institutional providers, mitigating concentration risk.

**Operational Risk Management** — Strict operational safeguards — permission controls, workflow separation, automated reconciliation, and wash-trading prevention — minimize execution errors and enhance system reliability.

## Why Vision Research?

Vision Research combines institutional asset-management pedigree with deep crypto-native engineering:

* **Arbitrage portfolio management** is led by a former Blackstone quant and portfolio manager at a long-standing systematic crypto fund, with expertise in arbitrage strategies and DeFi trading, and a former lecturer at Columbia University.
* **Alpha research and strategy design** is led by a quantitative strategist with 5+ years across centralized-exchange and on-chain markets, previously at Crypto.com after a multi-billion-dollar asset manager.
* **Off-chain systems** are built by a former CTO of a New York asset-management firm, specializing in low-latency architecture and high-frequency trading systems for institutional-grade execution.
* **On-chain engineering** is led by a full-stack developer with 8+ years of experience, including four in Web3 and prior work at Bytedance, focused on on-chain strategy engineering and protocol-level integration.

{% hint style="info" %}
Vision Research is an alias. We've excluded the curator's full name to mitigate alpha leaking. Neutral Trade has completed thorough due diligence on the team and its strategy.
{% endhint %}
