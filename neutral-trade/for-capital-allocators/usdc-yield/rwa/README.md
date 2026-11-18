---
description: >-
  RWA strategies on Neutral Trade trade regulated traditional markets, funded
  with USDC through a Neutral Strategy Vault.
---

# RWA

Real-world asset (RWA) strategies trade traditional, regulated markets: listed equities, fixed income, and exchange-traded derivatives. You deposit USDC into a Neutral Strategy Vault on Solana. The curator trades the strategy on traditional exchanges, and your position is recorded on-chain as vault shares.

RWA here means strategies that trade traditional markets. The vault does not hold tokenized assets.

RWA strategies add a return source that crypto-native strategies do not have. Their returns come from traditional markets, not from perpetual funding rates or price spreads between crypto exchanges.

{% hint style="info" %}
RWA strategies follow a traditional dealing calendar. Deposits and redemptions settle on scheduled dates, with notice periods, instead of the weekly schedule that most vaults use. Read the subscription terms on the strategy page before you deposit.
{% endhint %}

## Current Strategies

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Multi-Asset Volatility Arbitrage</strong></td><td>A systematic, cross-asset volatility strategy curated by D Research.</td><td><a href="multi-asset-volatility-arbitrage.md">multi-asset-volatility-arbitrage.md</a></td></tr></tbody></table>

| Strategy                                                                | Curator    | Return source                                                                    | Markets                                                                                                                                     | Dealing                                      |
| ----------------------------------------------------------------------- | ---------- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| [Multi-Asset Volatility Arbitrage](multi-asset-volatility-arbitrage.md) | D Research | Volatility risk premia, captured through relative value and volatility arbitrage | US-listed equity, fixed income, and volatility instruments, including digital-asset proxies such as Bitcoin ETFs. Venues: NASDAQ, NYSE, CME | Monthly subscriptions, quarterly redemptions |

## How RWA Differs From Crypto-Native Vaults

The table compares the current RWA strategy with the crypto-native strategy vaults. A future RWA strategy can have different terms.

| Topic               | Multi-Asset Volatility Arbitrage (RWA)                                                                  | Crypto-native strategy vaults                                                    |
| ------------------- | ------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| **Markets**         | Traditional exchanges with fixed trading hours                                                          | Crypto venues that trade 24/7                                                    |
| **Return source**   | Volatility risk premia in listed markets                                                                | Funding rates, basis, spreads, and crypto market signals                         |
| **Deposits**        | Monthly subscription, with a deadline 5 business days before the first business day of the month        | Batched and processed daily                                                      |
| **Redemptions**     | Quarterly, with 30 days notice and a gate that caps redemptions at 25% of the product's AUM per quarter | Weekly or twice weekly                                                           |
| **Minimum deposit** | 50,000 USDC                                                                                             | 100 USDC on most vaults                                                          |
| **Fees**            | 1% annual management fee, no performance fee, 0.3% withdrawal fee                                       | 1% annual management fee, a performance fee on most vaults, and a withdrawal fee |

## How It Works

1. **Subscribe.** Submit your USDC deposit before the monthly deadline. A deposit that misses the deadline waits for the next monthly cycle.
2. **Settlement.** The subscription settles after the start of the month. Your capital is then active in the strategy and you hold vault shares.
3. **Valuation.** The share price updates on scheduled valuation dates, not continuously.
4. **Redeem.** Submit a redemption request before the quarterly notice deadline. After settlement, USDC returns to the wallet that made the deposit.

The exact deadlines and settlement times are in the Subscription Terms on the [strategy page](multi-asset-volatility-arbitrage.md) and in the vault's Details view in the app.

## Key Risks

RWA strategies carry the risks in the [Risk Overview](../../risk-overview/), and some that are specific to traditional markets.

* **Market and volatility risk.** A volatility strategy can lose money when volatility rises sharply or when relative-value positions move apart. Losses can arrive quickly in a market shock.
* **Liquidity and redemption risk.** Redemptions are quarterly, need advance notice, and are subject to a gate. An exit can take longer than one quarter. Your capital stays exposed to the strategy until settlement.
* **Market-hours risk.** Traditional exchanges close overnight, on weekends, and on holidays. Positions cannot be adjusted while a market is closed, and prices can gap at the open.
* **Off-chain counterparty risk.** Capital that is deployed in traditional markets sits with traditional brokers and custodians. This is a different set of counterparties from the crypto venues that other vaults use.
* **Regulatory and access risk.** Traditional securities markets are regulated. A change in rules can restrict the instruments, the venues, or who can access the strategy. See [Regional Availability](../../../legal/regional-availability.md).
* **Platform and smart contract risk.** Deposits, withdrawals, and share accounting run through the Neutral Strategy Vault contracts. See [Security](../../../neutral-strategy-vaults/security.md) and [Vault Protections](../../../neutral-strategy-vaults/vault-protections.md).

## Who RWA Strategies Are Built For

RWA strategies are built for allocators who:

* Plan to hold for quarters, not weeks.
* Can meet a higher minimum deposit.
* Want a return source that does not depend on crypto funding rates or exchange spreads.
* Accept scheduled valuation and limited liquidity in exchange for access to that return source.

If you need weekly liquidity, look at [Market Neutral](../market-neutral/) strategies or [Neutral Autopilot](../../neutral-autopilot.md).

## Related Strategies

[CTA - Systematic Alpha](../directional/systematic-alpha.md) also trades US equity markets, through ETFs and equity index futures. It is listed under [Directional](../directional/) because it carries long market exposure, and it follows the weekly redemption schedule.

## Curator and Due Diligence

Every curator passes [Curator Selection](../../../curators/curator-selection.md) before a strategy is listed: a verified track record, a review of risk controls, and operational due diligence.

{% hint style="info" %}
D Research is an alias. We've excluded the curator's full name to mitigate alpha leaking. Neutral Trade has completed thorough due diligence on the team and its strategy.
{% endhint %}

## Fees and Terms

The current RWA strategy has a 1% annual management fee, no performance fee, and a 0.3% withdrawal fee. See [Fees + Redemption Period](../../../additional-info/fees-+-redemption-period.md) for how fees are charged. Minimums, deadlines, and fees for the vault are in its Details view in the app.

_Products referenced are not intended for individuals in the United States, Mainland China, Hong Kong, sanctioned, or other restricted jurisdictions. This page is for informational purposes only and does not constitute an offer, solicitation, or recommendation to buy or sell any financial instrument. These strategies involve significant risk, including possible loss of principal. See the_ [_Risk Warnings and Disclaimers Statement_](../../../legal/risk-warnings-and-disclaimers-statement.md)_._
