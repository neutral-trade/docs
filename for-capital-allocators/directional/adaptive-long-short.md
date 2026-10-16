---
description: >-
  Adaptive Long-Short is a systematic long-short crypto momentum strategy on
  Binance, curated by AdverseGuard Alpha, that rebalances on an hourly cycle.
hidden: true
---

# Adaptive Long-Short

## Overview

Adaptive Long-Short is a directional, systematic, multi-asset long-short crypto momentum strategy. It trades a diversified basket of liquid major cryptocurrencies and rebalances on an hourly cycle.

Its edge comes from combining multiple independent quantitative signals into a single, risk-aware portfolio. This lets the strategy adapt to changing market regimes and capture persistent trends across the crypto market. The strategy seeks a positive payoff asymmetry: winning positions compound, while downside risk is tightly controlled.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies">https://www.neutral.trade/strategies</a></td></tr></tbody></table>

## Key Facts

| Item                | Detail                                   |
| ------------------- | ---------------------------------------- |
| **Category**        | Directional                              |
| **Curator**         | AdverseGuard Alpha                       |
| **Deposit asset**   | USDC on Solana                           |
| **Minimum deposit** | To be confirmed                          |
| **Management fee**  | 1% per year                              |
| **Performance fee** | 35% of profit above your high-water mark |
| **Redemptions**     | Once weekly, on Friday                   |

The vault's Details view in the app shows the current terms. See [Fees + Redemption Period](../../additional-info/fees-+-redemption-period.md).

## How It Works

The strategy trades a diversified basket of liquid major cryptocurrencies through a systematic long-short approach, rebalancing on an hourly cycle.

**Multi-signal model.** A proprietary multi-signal system combines independent quantitative inputs. It generates internal fair-value estimates, identifies momentum opportunities, and detects breakdowns in correlations across markets. These signals identify shifts in market relationships and inform portfolio positioning as conditions change.

**Execution.** Execution algorithms use these internal fair values together with current liquidity conditions to optimise order timing, pricing, and sizing. This reduces slippage and market impact.

**Position sizing.** Disciplined position sizing and continuous risk controls support the objective: capture persistent trends and relative-value opportunities, let winning positions compound, and limit downside exposure.

#### Venues

**Centralized:** Binance

### Yield Sources

* Maker rebate
* Internal proprietary pricing and trading information
* Short-term cross-market correlation breakdown

## Risk Management

The strategy uses a stop-loss framework that catches risk at both the execution level and the portfolio level.

**Trading system controls.** The first layer operates directly within the trading application. It monitors real-time position exposure and triggers automated stop-loss actions at the strategy level, responding to adverse price moves before losses compound.

**Drawdown profile.** The maximum observed drawdown was -5.42%, recorded on October 10, 2025. The strategy has not breached this level since.

**Dynamic risk scaling.** Beyond stop-loss controls, the strategy's predictive model continuously monitors for adverse selection and directional risk. When risk conditions rise, activity is automatically scaled back or paused, prioritising capital preservation.

## Custody & Security

Depositor capital never leaves institutional custody. Funds are mirrored into a dedicated execution-only sub-account that the curator trades, but cannot withdraw to any external address.

| Layer            | Detail                                                                      |
| ---------------- | --------------------------------------------------------------------------- |
| Custody          | Ceffu (MirrorX) — Binance                                                   |
| Execution venue  | Binance                                                                     |
| Vault accounting | Fully on-chain: NAV, share mint/burn, high-water marks, fee accrual         |
| Blockchain       | Solana                                                                      |
| Vault program    | NT Bundle V1, audited by Halborn, Quantstamp, Offside Labs, and Adevar Labs |

Full details: [Security](../../neutral-strategy-vaults/security.md).

## Risk Factors

* **Directional exposure.** The strategy takes long and short positions on purpose. A move against its positions causes a loss, and drawdowns are an expected part of the return profile.
* **Model risk.** Returns depend on momentum and correlation signals that can weaken or break when market structure changes.
* **Liquidity and execution risk.** In stressed markets, positions may not be exitable at expected prices.
* **Venue concentration.** Execution is concentrated on a single venue (Binance).
* **No guarantee of returns.** Past drawdown levels do not limit future losses.

The [Risk Overview](../risk-overview/) covers these risks in more detail.

## Why AdverseGuard Alpha?

AdverseGuard Alpha operates at the intersection of traditional finance and digital assets, deploying a multi-strategy quantitative framework across global markets. It also curates the [Mid-frequency Market Making](../market-neutral/mid-frequency-market-making.md) strategy on Neutral Trade.

The team has deep roots in high-frequency trading, asset management, and exchange infrastructure, with decades of combined institutional experience from firms including Tower Research, Citadel, Susquehanna (SIG), Kronos Research, Point72, State Street, RBC, and J.P. Morgan.

{% hint style="info" %}
AdverseGuard Alpha is an alias. We've excluded the curator's full name to mitigate alpha leaking. Neutral Trade has completed thorough due diligence on the team and its strategy.
{% endhint %}

_Products referenced are not intended for individuals in the United States, Mainland China, Hong Kong, sanctioned, or other restricted jurisdictions. This page is for informational purposes only and does not constitute an offer, solicitation, or recommendation to buy or sell any financial instrument. Digital-asset strategies involve significant risk, including possible loss of principal. See the_ [_Risk Warnings and Disclaimers Statement_](../../legal/risk-warnings-and-disclaimers-statement.md)_._
