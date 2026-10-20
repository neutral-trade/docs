---
description: >-
  Meridian Liquidity Provider (MLP) is a market-neutral market making strategy
  between Meridian and Bitget, managed by Kappa Labs with Copper ClearLoop.
---

# Meridian Liquidity Provider

## Overview

Meridian Liquidity Provider (MLP) is a market making strategy between Meridian perpetuals and Bitget. Kappa Labs manages the strategy. It provides liquidity on one venue and manages the offsetting exposure on the other, so returns come from spread capture and not from market direction.

You deposit USDe. Collateral for the exchange leg stays in off-exchange custody with Copper ClearLoop.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT ON NEUTRAL TRADE</strong></td><td><a href="https://www.neutral.trade/strategies/meridian-liquidity-provider">https://www.neutral.trade/strategies/meridian-liquidity-provider</a></td></tr><tr><td><strong>MLP VAULT ON MERIDIAN</strong></td><td><a href="https://app.meridian.xyz/vault">https://app.meridian.xyz/vault</a></td></tr></tbody></table>

## Key Facts

| Item                       | Detail                                         |
| -------------------------- | ---------------------------------------------- |
| **Strategy type**          | Market neutral: cross-venue market making      |
| **Managed by**             | Kappa Labs                                     |
| **Venues**                 | Meridian (perpetuals) and Bitget               |
| **Custody and settlement** | Copper ClearLoop, with off-exchange settlement |
| **Deposit asset**          | USDe                                           |
| **Network**                | Robinhood Chain                                |
| **Management fee**         | 1% per year                                    |

This vault runs on a different vault contract from the Solana strategy vaults. Its performance fee, minimums, and withdrawal timing are shown in the vault's Details view in the app. If a figure on this page differs from the Details view, the Details view is correct.

## How It Works

1. **Deposit USDe.** You deposit USDe into the MLP vault and receive vault shares.
2. **Kappa Labs quotes on Meridian.** The strategy places buy and sell quotes on Meridian perpetual markets. This gives Meridian traders liquidity.
3. **The exposure is hedged on Bitget.** When a quote is filled, the strategy takes the offsetting position on Bitget. The book stays close to market neutral.
4. **The spread is the return.** The strategy earns the difference between the price it quotes on one venue and the price it hedges at on the other.
5. **Withdraw.** You redeem on the vault's own terms, shown in the app.

## What You Earn

A deposit in the MLP vault earns from these sources:

| Source                    | How it reaches you                                                     |
| ------------------------- | ---------------------------------------------------------------------- |
| **Market making returns** | Spread capture from the strategy, reflected in the vault's share price |
| **Base USDe rate**        | Automatically distributed to the vault                                 |
| **Ethena rewards**        | Earned continuously for your time in the vault                         |
| **Meridian Points**       | Earned continuously for your time in the vault                         |

The rewards and points programs are run by Ethena and Meridian. Their terms can change, and Neutral Trade does not control them. See the [MLP vault page on Meridian](https://app.meridian.xyz/vault) for the current programs.

## Custody & Security

* **Off-exchange settlement.** Collateral for the Bitget leg is held with [Copper](https://copper.co) and mirrored to the exchange through ClearLoop. The assets stay with the custodian, not on the exchange balance sheet. Trades settle off-exchange.
* **Trading access only.** Kappa Labs has execution permissions. It cannot withdraw vault capital to an arbitrary external address.
* **A separate vault contract.** The four audits on the [Security](../../../neutral-strategy-vaults/security.md) page cover the Solana vault program. The MLP vault uses a different contract on Robinhood Chain.

## Risk Factors

Market making hedges market direction. It does not remove risk.

* **Adverse selection.** The strategy can be filled on the wrong side of a fast move before it can hedge. This erodes spread income and can cause a loss.
* **Hedge and basis risk.** The price on Meridian and the price on Bitget can move apart. A hedge can be late, partial, or more expensive than expected.
* **Venue and counterparty risk.** Meridian, Bitget, or the custodian can fail or stop operating while they hold deployed capital. Off-exchange custody reduces the exposure to Bitget. It does not remove venue risk on Meridian.
* **Stablecoin risk.** The vault holds USDe. A loss of the USDe peg, or a change in its yield, affects the value of your position.
* **Smart contract and network risk.** The vault contract, Meridian, and Robinhood Chain carry smart-contract and network risk.
* **Liquidity risk.** Redemptions follow the vault's own terms. You stay exposed to the share price until settlement.

Read [Market & Strategy Risk](../../risk-overview/market-and-strategy-risk.md) and [Venue, Counterparty & Curator Risk](../../risk-overview/venue-counterparty-and-curator-risk.md) for the full picture.

## Common Questions

**What is the Meridian Liquidity Provider vault?**

A market-neutral vault. Kappa Labs makes markets on Meridian perpetuals and hedges on Bitget.

**Who holds the collateral?**

Collateral for the exchange leg is held with Copper and settled off-exchange through ClearLoop.

**Which asset do I deposit?**

USDe, on Robinhood Chain.

**Are returns guaranteed?**

No. The vault can lose money. Past performance does not indicate future results.

_Products referenced are not intended for individuals in the United States, Mainland China, Hong Kong, sanctioned, or other restricted jurisdictions. This page is for informational purposes only and does not constitute an offer, solicitation, or recommendation to buy or sell any financial instrument. Digital-asset strategies involve significant risk, including possible loss of principal. See the_ [_Risk Warnings and Disclaimers Statement_](../../../legal/risk-warnings-and-disclaimers-statement.md)_._
