---
description: >-
  CTA - Longshort Alpha is a systematic long-short crypto perpetuals strategy
  curated by C Research, with low correlation to peer crypto funds.
---

# CTA - Longshort Alpha

## Overview

CTA Longshort Alpha is a systematic book that takes long and short positions across crypto perpetual futures. Rather than betting on market direction, it builds an offsetting portfolio across a broad universe, so that returns from different factors are combined and hedged for a higher Sharpe ratio.

The edge is contrarian: the strategy profits from **market crowdedness and extreme sentiment shifts**, positioning against the crowd when it is offside and exiting as prices normalise. Signals are cross-validated across multiple trading venues and asset classes.

The curator monitors over 500 symbols and trades a universe of roughly the top 30 perpetuals. The book has recorded a **single-digit correlation to peer crypto funds**, making it a genuine diversifier alongside both directional and market-neutral allocations.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies/cta-longshort-alpha">https://www.neutral.trade/strategies/cta-longshort-alpha</a></td></tr></tbody></table>

## Key Facts

| Item                | Detail                                   |
| ------------------- | ---------------------------------------- |
| **Curator**         | C Research                               |
| **Deposit asset**   | USDC on Solana                           |
| **Minimum deposit** | 100 USDC                                 |
| **Management fee**  | 1% per year                              |
| **Performance fee** | 30% of profit above your high-water mark |
| **Withdrawal fee**  | 0.3%                                     |
| **Redemptions**     | Once weekly, on Friday                   |

The vault's Details view in the app shows the current terms. See [Fees + Redemption Period](../../additional-info/fees-+-redemption-period.md).

## How It Works

Several uncorrelated return drivers run in parallel, and new ones are added over time to reduce reliance on any single market regime.

### Active Strategies

| Strategy                                  | What it does                                                                                                                                                    |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Intra-day momentum**                    | Captures inefficiencies during periods of market crowdedness. Robustness cross-validated across multiple trading venues for consistent risk-return.             |
| **Funding collection**                    | Systematically harvests funding-rate spreads across perpetual futures.                                                                                          |
| **Mean reversion and volatility selling** | Captures mean-reversion patterns within a risk-constrained universe, generating returns in low-volatility regimes while avoiding left-skewed adverse selection. |

### In Development

* **Higher-frequency alpha.** Shorter-term momentum signals, particularly effective during persistent intraday price movement.
* **Cross-asset / cross-exchange alpha.** Extends signal generation across asset classes to identify intermarket dislocations and liquidity flows.

### Trading Profile

| Metric                           | Detail                                           |
| -------------------------------- | ------------------------------------------------ |
| Primary venue                    | Binance perpetual futures                        |
| Trading universe                 | \~Top 30 perpetuals (over 500 symbols monitored) |
| Correlation to peer crypto funds | Under 10%                                        |
| Trading hours                    | Continuous, 24/7                                 |

***

## Risk Management

**Model-level risk diversification.** The book is run largely long-short, minimising net directional beta so returns are driven by a combination of hedged factors rather than market direction, keeping correlation to crypto beta low. A proprietary Barra-style risk model continuously monitors factor loadings, maintaining smart-beta exposure tilted toward yield-generating factors while limiting unintended systematic risk.

**24/7 monitoring.** A fully tested real-time alerting system provides round-the-clock surveillance of all positions and system health. Discretionary intervention is applied only in a disciplined and conservative manner, as a safety measure rather than a source of returns.

**Stress-tested through live events.** The book traded through the October 2025 market-wide liquidation cascade, the largest in crypto history, which stress-tested its execution infrastructure, and through the July 2024 altcoin drawdown of over 40%, which tested cross-sectional positioning and risk controls.

| Risk parameter       | Value |
| -------------------- | ----- |
| Vault drawdown limit | `15%` |
| Vault leverage       | 2x-3x |

## Custody & Security

Depositor capital never leaves institutional custody. Funds are mirrored into a dedicated execution-only sub-account that the curator trades, but cannot be withdrawn to any external address.

| Layer            | Detail                                                                                                   |
| ---------------- | -------------------------------------------------------------------------------------------------------- |
| Custody          | Ceffu (MirrorX) — Binance                                                                                |
| Execution venue  | Binance perpetual futures                                                                                |
| Account model    | Managed sub-account. The curator trades at its own fee tier; margin remains within the custody perimeter |
| Vault accounting | Fully on-chain: NAV, share mint/burn, high-water marks, fee accrual                                      |
| Blockchain       | Solana                                                                                                   |
| Vault program    | NT Bundle V1, audited by Halborn, Quantstamp, Offside Labs, and Adevar Labs                              |

Full details: [Security](../../neutral-strategy-vaults/security.md).

## Risk Factors

* **Long-short is not risk-free.** The book minimises net directional beta, but relative-value positions can move against the strategy. Drawdowns are expected, and larger losses remain possible.
* **Model risk.** Returns depend on statistical relationships (crowdedness and mean-reversion signals) that can degrade or break down as market structure changes.
* **Leverage risk.** Leverage amplifies both gains and losses; vault drawdown scales roughly linearly with the leverage applied.
* **Liquidity and adverse selection risk.** In stressed markets, positions may not be exitable at expected prices. Liquidation cascades can widen realised losses beyond modelled levels.
* **Short track record.** The live book launched in October 2024, a relatively short history covering a limited range of market regimes.
* **Discretionary intervention.** While the strategy is systematic, the team may intervene manually in exceptional circumstances, introducing a degree of human judgement.
* **Execution, technology and venue risk.** The strategy depends on connectivity, exchange availability and correct system behaviour, and concentrates execution on a single primary venue.
* **No guarantee of returns.** Target figures are objectives, not commitments.

The [Risk Overview](../risk-overview/) covers these risks in more detail.

## Why C Research?

C Research is a quantitative digital-asset trading team based in Asia. The team formed in mid-2024 and launched its live book in October 2024, and trades predominantly its **own capital**. Roughly 90% of the book is proprietary, aligning the team directly with allocator outcomes.

The team's background is in systematic quantitative research at established global quant funds, spanning equities and commodities as well as digital assets, and it applies that institutional research framework to crypto markets.

{% hint style="info" %}
C Research is an alias. We've excluded the curator's full name to mitigate alpha leaking. Neutral Trade has completed thorough due diligence on the team and its strategy.
{% endhint %}

{% hint style="info" %}
Neutral Trade conducts due diligence on every curator, but does not guarantee strategy performance. Allocate only what you can afford to have at risk.
{% endhint %}

_Products referenced are not intended for individuals in the United States, Mainland China, Hong Kong, sanctioned, or other restricted jurisdictions. This page is for informational purposes only and does not constitute an offer, solicitation, or recommendation to buy or sell any financial instrument. Digital-asset strategies involve significant risk, including possible loss of principal. See the_ [_Risk Warnings and Disclaimers Statement_](../../legal/risk-warnings-and-disclaimers-statement.md)_._
