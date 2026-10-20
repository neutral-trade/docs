---
description: >-
  Directional (CTA) strategies on Neutral Trade: systematic trend, mean
  reversion, and long-short strategies in crypto and US equity markets.
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

# Directional

Directional strategies take market exposure on purpose. Quantitative signals decide when a strategy is long, short, or out of the market. Returns depend on those signals being right more often than they are wrong, so drawdowns are a normal part of how these strategies work.

Unlike market-neutral strategies, directional strategies have returns that move with their markets to some degree. Expect higher variance and a wider range of monthly results.

All strategies in this category are run by external curator teams that have passed Neutral Trade's [Curator Selection](../../../curators/curator-selection.md) process, including a review of the performance track record, a Sharpe ratio assessment, and operational due diligence.

## Current Strategies

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>CTA - Adaptive Alpha</strong></td><td>Trend following and mean reversion on major crypto derivatives, curated by Atlas Research.</td><td><a href="cta-adaptive-alpha.md">cta-adaptive-alpha.md</a></td></tr><tr><td><strong>CTA - Systematic Alpha</strong></td><td>A long-only systematic strategy on US equities, curated by Hyperithm.</td><td><a href="systematic-alpha.md">systematic-alpha.md</a></td></tr><tr><td><strong>CTA - Longshort Alpha</strong></td><td>A long-short book across crypto perpetual futures, curated by C Research.</td><td><a href="cta-longshort-alpha.md">cta-longshort-alpha.md</a></td></tr></tbody></table>

| Strategy                                        | Curator        | Markets                                              | Approach                                                                                           | Stated risk limits                                                                                           | Performance fee | Redemptions |
| ----------------------------------------------- | -------------- | ---------------------------------------------------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | --------------- | ----------- |
| [CTA - Adaptive Alpha](cta-adaptive-alpha.md)   | Atlas Research | BTC, ETH, XRP, and SOL derivatives on Binance        | Switches between trend following and mean reversion. Long and short.                               | Daily maximum drawdown target of about 10%. A 20% daily drawdown pauses the strategy for a full risk review. | 25%             | Once weekly |
| [CTA - Systematic Alpha](systematic-alpha.md)   | Hyperithm      | Liquid US equity ETFs and equity index futures       | Mean reversion and trend following. Long-only. About 30% of capital is exposed on average.         | Targets a single-digit average drawdown.                                                                     | 25%             | Once weekly |
| [CTA - Longshort Alpha](cta-longshort-alpha.md) | C Research     | About the top 30 crypto perpetual futures on Binance | Largely long-short. Intraday momentum, funding collection, mean reversion, and volatility selling. | Vault drawdown limit of 15%. Leverage of 2x to 3x.                                                           | 30%             | Once weekly |

Some curators operate under a publication alias. Neutral Trade completes the same due diligence on the legal entity behind each alias.

## How Directional Strategies Earn

| Return source              | How it works                                                                                                                                                             | Strategies                                                          |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------- |
| **Trend following**        | The strategy enters when a market forms a trend and exits at a profit target or when the regime changes. It earns when a market moves strongly in one direction.         | CTA - Adaptive Alpha, CTA - Systematic Alpha                        |
| **Mean reversion**         | The strategy enters when a price moves away from a reference level and exits when the price reverts. It earns in volatile, range-bound, and corrective markets.          | CTA - Adaptive Alpha, CTA - Systematic Alpha, CTA - Longshort Alpha |
| **Long-short positioning** | The strategy holds offsetting long and short positions across many assets. It earns from crowded positioning and extreme sentiment shifts, with low net market exposure. | CTA - Longshort Alpha                                               |

## The Three Strategies Are Different

Directional is a broad category. Compare the strategies before you allocate.

* **CTA - Adaptive Alpha** can be long or short major crypto assets. It trades about 6 times per asset per day and runs 24/7.
* **CTA - Systematic Alpha** trades US equity markets, not crypto. It is long-only and holds positions for 3 to 5 days. It can lose money in a sustained bear market in US equities.
* **CTA - Longshort Alpha** runs a largely long-short book with low net market exposure. Its returns still depend on its signals, and relative-value positions can move against it.

## Key Risks

* **Market risk.** These strategies carry market exposure. A move against the position causes a loss.
* **Drawdowns.** Drawdowns are an expected part of the return profile, not a malfunction. Review the maximum drawdown and the volatility of each vault before you allocate.
* **Model risk.** Returns depend on statistical relationships that can weaken or break when market structure changes.
* **Leverage and liquidation.** Leverage amplifies gains and losses. A sharp adverse move can trigger forced liquidation.
* **Venue and counterparty risk.** An exchange or custodian can fail while it holds deployed capital.

Read [Market & Strategy Risk](../../risk-overview/market-and-strategy-risk.md) and [Venue, Counterparty & Curator Risk](../../risk-overview/venue-counterparty-and-curator-risk.md) for the full picture.

## Where Directional Fits

Directional strategies are a higher-variance complement to a [Market Neutral](../market-neutral/) core. [Neutral Autopilot](../../neutral-autopilot.md) applies the same idea: it is primarily market-neutral and limits directional strategies to 5% of its portfolio.

## Fees and Redemptions

* **Management fee.** 1% per year on every current strategy vault.
* **Performance fee.** Directional vaults also charge a performance fee. It applies only to profit above your own high-water mark.
* **Redemptions.** Directional vaults redeem once weekly, on Friday. You can submit a request on any day.

See [Fees + Redemption Period](../../../additional-info/fees-+-redemption-period.md) for the fee table and the full schedule. Minimums, capacity, and fees for each vault are in its Details view in the app.

_Products referenced are not intended for individuals in the United States, Mainland China, Hong Kong, sanctioned, or other restricted jurisdictions. This page is for informational purposes only and does not constitute an offer, solicitation, or recommendation to buy or sell any financial instrument. These strategies involve significant risk, including possible loss of principal. See the_ [_Risk Warnings and Disclaimers Statement_](../../../legal/risk-warnings-and-disclaimers-statement.md)_._
