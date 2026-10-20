---
description: >-
  Neutral Trade's first SOL Yield Vault: an institutional options market making
  strategy on OKX, curated by Xanthas, whose returns are used to buy more SOL.
---

# Options Market Making (SOL)

## Overview

Options Market Making (SOL) is Neutral Trade's first SOL Yield Vault. You deposit SOL, and the vault runs the same institutional options market making strategy as our [Options Market Making](../usdc-yield/market-neutral/options-market-making.md) vault, curated by Xanthas on OKX. The strategy's returns are used to buy more SOL, so the vault aims to grow the number of SOL you hold.

The strategy targets volatility and relative-value opportunities through continuous options market making and multi-leg options trading. Its returns come from volatility and relative-value capture, not from the direction of the underlying market.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies/options-mm-sol">https://www.neutral.trade/strategies/options-mm-sol</a></td></tr></tbody></table>

## Key Facts

| Item                | Detail                                   |
| ------------------- | ---------------------------------------- |
| **Category**        | SOL Yield                                |
| **Curator**         | Xanthas                                  |
| **Deposit asset**   | SOL on Solana (native SOL or wSOL)       |
| **Minimum deposit** | 1 SOL                                    |
| **Management fee**  | 1% per year                              |
| **Performance fee** | 30% of profit above your high-water mark |
| **Withdrawal fee**  | 0.3%                                     |
| **Redemptions**     | To be confirmed                          |

The vault's Details view in the app shows the current terms. See [Fees + Redemption Period](../../additional-info/fees-+-redemption-period.md).

## How It Works

1. **You deposit SOL.** The app accepts native SOL, wrapped SOL (wSOL), or both, and wraps native SOL for you.
2. **The strategy trades.** Xanthas runs an automated options market making system on OKX. It quotes across the volatility surface, with a particular edge in multi-leg structures such as calendars, butterflies, verticals and risk reversals, sourced through institutional RFQ networks alongside order-book quoting. Directional exposure from the options book is hedged with perpetual futures.
3. **Returns buy more SOL.** The strategy's returns are used to buy more SOL for the vault, so your share of the vault is measured, and grows, in SOL.

The core engine is built around an arbitrage-free eSSVI volatility surface and a Bates-Kou jump-diffusion model calibrated to crypto's asymmetric return profile.

### Venues

**Centralized:** OKX, with off-exchange custody and settlement through Copper.

### Yield Sources

* **Variance risk premium:** captured through short-dated volatility selling.
* **Relative-value capture:** edge from trading multi-leg options structures, sourced through institutional RFQ networks alongside order-book quoting.

## Risk Factors

**SOL price exposure:** Your position is held in SOL. The vault aims to increase the number of SOL you hold, but the USD value of your position moves with the SOL price, up and down.

**Volatility and jump risk:** The options book is hedged against price direction but keeps exposure to changes in implied volatility (vega) and to large sudden price moves (gamma and jumps). A volatility spike or a sharp market move can cause mark-to-market losses, which reduce the number of SOL in the vault. Mitigations: a jump-diffusion pricing model that prices the likelihood of sharp moves, and dedicated vega management.

**Adverse selection risk:** As a market maker, the strategy can be filled on the wrong side of an informed move. Mitigations: the jump-diffusion pricing model reduces pricing error on out-of-the-money options.

**Hedging and funding risk:** Directional exposure is hedged with perpetual futures. Funding costs can be positive or negative, hedge adjustments have transaction costs, and perpetual positions are subject to exchange margin requirements and Auto-Deleveraging (ADL). Mitigations: charm-aware hedging reduces how often the hedge must be adjusted, and the risk framework includes funding rate hedging.

**Counterparty and exchange risk:** Trading on a centralized venue creates exposure to venue failure, insolvency, or operational disruption. Mitigations: off-exchange custody and settlement through Copper, so assets stay with the custodian and not on the exchange balance sheet.

**Operational and execution risk:** The strategy runs as automated software through the exchange API and depends on connectivity and infrastructure. Mitigations: exchange-native market-maker protection, cancel-on-disconnect, and independent software circuit breakers.

The [Risk Overview](../risk-overview/) covers these risks in more detail.

## Why Xanthas?

Xanthas is an institutional crypto options market maker. It also curates the [Options Market Making](../usdc-yield/market-neutral/options-market-making.md) vault on Neutral Trade, which runs the same strategy in USDC and has been live since 14 July 2026.

{% hint style="info" %}
Xanthas is an alias. We've excluded the curator's full name to mitigate alpha leaking. Neutral Trade has completed thorough due diligence on the team and its strategy.
{% endhint %}

_Products referenced are not intended for individuals in the United States, Mainland China, Hong Kong, sanctioned, or other restricted jurisdictions. This page is for informational purposes only and does not constitute an offer, solicitation, or recommendation to buy or sell any financial instrument. Digital-asset strategies involve significant risk, including possible loss of principal. See the_ [_Risk Warnings and Disclaimers Statement_](../../legal/risk-warnings-and-disclaimers-statement.md)_._
