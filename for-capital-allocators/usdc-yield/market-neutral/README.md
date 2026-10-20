---
description: >-
  Market-neutral crypto strategies on Neutral Trade: funding arbitrage,
  cross-venue arbitrage, market making, and options, hedged against direction.
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

# Market Neutral

Market-neutral strategies hold offsetting long and short positions, so their returns do not depend on the market going up or down. They earn from structural sources: funding rates, price differences between venues, market-making spreads, and volatility premia.

These strategies are built for allocators who put consistency and capital preservation first. They also form the core of [Neutral Autopilot](../../neutral-autopilot.md).

{% hint style="warning" %}
Market neutral means that a strategy hedges market direction. It does not mean that the strategy cannot lose money. See [Market & Strategy Risk](../../risk-overview/market-and-strategy-risk.md).
{% endhint %}

## Current Strategies

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Hyperliquid Funding Arb</strong></td><td>Delta-neutral spot and perpetual positions on Hyperliquid that collect funding payments.</td><td><a href="hyperliquid-funding-arb.md">hyperliquid-funding-arb.md</a></td></tr><tr><td><strong>Delta Neutral Arbitrage</strong></td><td>Multi-venue arbitrage across centralized and decentralized exchanges, curated by Velox Trading Group.</td><td><a href="delta-neutral-arbitrage.md">delta-neutral-arbitrage.md</a></td></tr><tr><td><strong>Options Market Making</strong></td><td>Delta-hedged Bitcoin options market making, curated by Xanthas.</td><td><a href="options-market-making.md">options-market-making.md</a></td></tr><tr><td><strong>Mid-frequency Market Making</strong></td><td>Liquidity provision on Binance perpetual futures, curated by AdverseGuard Alpha.</td><td><a href="mid-frequency-market-making.md">mid-frequency-market-making.md</a></td></tr><tr><td><strong>HFT Multi-factor</strong></td><td>High-frequency signals and market making on Binance, curated by Vision Research.</td><td><a href="hft-multi-factor.md">hft-multi-factor.md</a></td></tr><tr><td><strong>Meridian Liquidity Provider</strong></td><td>Market making between Meridian and Bitget, managed by Kappa Labs.</td><td><a href="meridian-liquidity-provider.md">meridian-liquidity-provider.md</a></td></tr></tbody></table>

| Strategy                                                      | Curator             | Main return source                                                                           | Venues                                                                         | Redemptions                 |
| ------------------------------------------------------------- | ------------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ | --------------------------- |
| [Hyperliquid Funding Arb](hyperliquid-funding-arb.md)         | Neutral Trade       | Perpetual funding payments, with a 10% allocation to the Hyperliquidity Provider (HLP) vault | Hyperliquid                                                                    | Twice weekly                |
| [Delta Neutral Arbitrage](delta-neutral-arbitrage.md)         | Velox Trading Group | Cross-venue arbitrage, funding and basis arbitrage, and DeFi market making                   | Multiple venues, including Binance, OKX, Bybit, Gate, Hyperliquid, and Lighter | Twice weekly                |
| [Options Market Making](options-market-making.md)             | Xanthas             | Bitcoin options volatility and relative value, hedged with perpetual futures                 | OKX                                                                            | Twice weekly                |
| [Mid-frequency Market Making](mid-frequency-market-making.md) | AdverseGuard Alpha  | Bid-ask spread and maker rebates on ETHUSDT perpetual futures                                | Binance                                                                        | Once weekly                 |
| [HFT Multi-factor](hft-multi-factor.md)                       | Vision Research     | High-frequency trading signals and market making                                             | Binance                                                                        | Once weekly                 |
| [Meridian Liquidity Provider](meridian-liquidity-provider.md) | Kappa Labs          | Spread capture from market making between Meridian perpetuals and Bitget                     | Meridian, Bitget                                                               | Own terms, shown in the app |

Meridian Liquidity Provider accepts USDe on Robinhood Chain and runs on a different vault contract from the other strategies. Its collateral for the exchange leg is held with Copper ClearLoop.

Some curators operate under a publication alias. Neutral Trade completes the same due diligence on the legal entity behind each alias. See [Curator Selection](../../../curators/curator-selection.md).

## How Market-Neutral Strategies Earn

| Return source                             | How it works                                                                                                                                                       | Strategies                                                                 |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------- |
| **Funding rate capture**                  | The strategy holds a spot long and a perpetual short on the same asset. When funding is positive, the short position receives payments from leveraged longs.       | Hyperliquid Funding Arb, Delta Neutral Arbitrage                           |
| **Cross-venue and basis arbitrage**       | The strategy buys on one venue and sells on another when the same asset trades at different prices, or trades the gap between spot and futures.                    | Delta Neutral Arbitrage                                                    |
| **Market making**                         | The strategy quotes both sides of the order book and earns the bid-ask spread and maker rebates. Models scale quotes back when a large directional move is likely. | Mid-frequency Market Making, HFT Multi-factor, Meridian Liquidity Provider |
| **Options volatility and relative value** | The strategy sells short-dated volatility and trades multi-leg options structures. Perpetual futures hedge the directional exposure.                               | Options Market Making                                                      |
| **Short-horizon signals**                 | Machine-learning factor models trade momentum and mean reversion over short horizons.                                                                              | HFT Multi-factor                                                           |

Each strategy page explains what the strategy trades, where the return comes from, and what can break it.

## Key Risks

Hedging removes market direction. It does not remove risk.

* **Funding reversal.** Funding can turn negative and stay negative. A funding strategy then pays instead of receives.
* **Basis and spread risk.** A price gap can widen before it converges, and can stay dislocated for longer than a position can be held.
* **Adverse selection.** A market maker can be filled on the wrong side of a large move, which erodes spread income.
* **Volatility and jump risk.** An options book that is hedged for direction still loses when implied volatility spikes or the underlying price jumps.
* **Leverage and liquidation.** Some strategies use leverage. A sharp move can trigger forced liquidation or auto-deleveraging on perpetual futures.
* **Venue and counterparty risk.** An exchange, protocol, or custodian can fail while it holds deployed capital.

Read [Market & Strategy Risk](../../risk-overview/market-and-strategy-risk.md) and [Venue, Counterparty & Curator Risk](../../risk-overview/venue-counterparty-and-curator-risk.md) for the full picture.

## How Your Capital Is Controlled

* **Trading access only.** Curators can trade. They cannot withdraw your deposit. Every movement is restricted to pre-approved contracts and venues.
* **Off-exchange settlement.** Centralized-exchange positions settle off-exchange through Copper (ClearLoop) and Ceffu (MirrorX), which reduces exposure to an exchange failure.
* **Multi-party approval.** On-chain operations run through Fordefi, with an MPC workspace, a policy engine, an admin quorum, and a 12-hour timelock on smart contract changes.
* **Audits.** The Solana vault program has four independent audits: Halborn, Quantstamp, Offside Labs, and Adevar Labs. The reports are public on the [Security](../../../neutral-strategy-vaults/security.md) page.

These controls limit operational and platform risk. They do not make a losing strategy profitable. See [Vault Protections](../../../neutral-strategy-vaults/vault-protections.md).

## Fees and Redemptions

* **Management fee.** 1% per year on every current strategy vault.
* **Performance fee.** Most market-neutral vaults also charge a performance fee of 20% to 35%. It applies only to profit above your own high-water mark.
* **Redemptions.** Market-neutral vaults on Solana redeem once weekly (Friday) or twice weekly (Monday and Friday). You can submit a request on any day.

See [Fees + Redemption Period](../../../additional-info/fees-+-redemption-period.md) for the fee table and the full schedule. Minimums, capacity, and fees for each vault are in its Details view in the app.

## Prefer One Deposit?

[Neutral Autopilot](../../neutral-autopilot.md) allocates across these strategies for you and rebalances as conditions change.

_Products referenced are not intended for individuals in the United States, Mainland China, Hong Kong, sanctioned, or other restricted jurisdictions. This page is for informational purposes only and does not constitute an offer, solicitation, or recommendation to buy or sell any financial instrument. Digital-asset strategies involve significant risk, including possible loss of principal. See the_ [_Risk Warnings and Disclaimers Statement_](../../../legal/risk-warnings-and-disclaimers-statement.md)_._
