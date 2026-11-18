---
description: >-
  Market-neutral strategies on Neutral Marketplace: newer strategies from
  trading firms, hedged against market direction.
---

# Market Neutral

Market-neutral strategies hold offsetting positions, so their returns do not depend on the market going up or down. They earn from structural sources such as market-making spreads, funding rates and price differences between venues.

The strategies in this category are listed on [Neutral Marketplace](../). They passed basic due diligence: we met the team, we understand the strategy, and we completed full KYB on the firm. Neutral Trade has not yet tested them with its own capital, and [Neutral Autopilot](../../neutral-autopilot.md) does not allocate to them.

{% hint style="warning" %}
**A Marketplace listing is not an endorsement of performance.** Market neutral means that a strategy hedges market direction. It does not mean that the strategy cannot lose money. Deposit only what you can afford to lose.
{% endhint %}

## Current Strategies

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Meridian Liquidity Provider</strong></td><td>Market making between Meridian and Bitget, managed by Kappa Labs.</td><td><a href="meridian-liquidity-provider.md">meridian-liquidity-provider.md</a></td></tr></tbody></table>

| Strategy                                                      | Curator    | Main return source                                                       | Venues           | Redemptions                 |
| ------------------------------------------------------------- | ---------- | ------------------------------------------------------------------------ | ---------------- | --------------------------- |
| [Meridian Liquidity Provider](meridian-liquidity-provider.md) | Kappa Labs | Spread capture from market making between Meridian perpetuals and Bitget | Meridian, Bitget | Own terms, shown in the app |

Meridian Liquidity Provider accepts USDe on Robinhood Chain and runs on a different vault contract from the Solana strategy vaults. Its collateral for the exchange leg is held with Copper ClearLoop.

## Key Risks

* **Adverse selection.** A market maker can be filled on the wrong side of a large move, which erodes spread income.
* **Basis and spread risk.** A price gap between venues can widen before it converges.
* **Leverage and liquidation.** A sharp move can trigger forced liquidation or auto-deleveraging on perpetual futures.
* **Venue and counterparty risk.** An exchange, protocol, or custodian can fail while it holds deployed capital.
* **Short record.** A newer strategy has a shorter record, so its results are less certain.

Read [Market & Strategy Risk](../../risk-overview/market-and-strategy-risk.md) and [Venue, Counterparty & Curator Risk](../../risk-overview/venue-counterparty-and-curator-risk.md) for the full picture.

_Products referenced are not intended for individuals in the United States, Mainland China, Hong Kong, sanctioned, or other restricted jurisdictions. This page is for informational purposes only and does not constitute an offer, solicitation, or recommendation to buy or sell any financial instrument. Digital-asset strategies involve significant risk, including possible loss of principal. See the_ [_Risk Warnings and Disclaimers Statement_](../../../legal/risk-warnings-and-disclaimers-statement.md)_._
