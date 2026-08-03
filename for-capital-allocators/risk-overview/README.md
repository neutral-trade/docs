---
description: What can go wrong, who bears it, and where each risk is addressed.
---

# Risk Overview

Every strategy on Neutral Trade involves risk. The [Security](../../neutral-strategy-vaults/security.md) and [Vault Protections](../../neutral-strategy-vaults/vault-protections.md) pages describe the controls that protect your capital at the infrastructure level. This section covers the other half of the picture: the risks that remain after those controls — the ones you accept when you allocate to any strategy.

{% hint style="warning" %}
Nothing on Neutral Trade is a savings account, an insured deposit, or a guaranteed-return product. Every strategy can lose money, including in calm market conditions. Only deposit what you can afford to place at risk.
{% endhint %}

### The Five Risk Categories

| Category                           | What it covers                                                                                                                                  | Where it's addressed                                                                                                                                                    |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Market & strategy risk**         | The strategy itself loses money: spreads move the wrong way, funding rates flip, execution slips, models misfire.                               | [Market & Strategy Risk](market-and-strategy-risk.md)                                                                                                                   |
| **Venue & counterparty risk**      | An execution venue, exchange, external protocol, or curator fails while holding or managing deployed capital.                                   | [Venue, Counterparty & Curator Risk](venue-counterparty-and-curator-risk.md)                                                                                            |
| **Liquidity & redemption risk**    | Your exit takes longer, or completes at a worse price, than you expected — lockups, redemption periods, and stressed markets all affect timing. | This page, below                                                                                                                                                        |
| **Platform & smart contract risk** | A flaw in the vault contracts, key compromise, or an error in NAV reporting.                                                                    | [Security](../../neutral-strategy-vaults/security.md) and [Vault Protections](../../neutral-strategy-vaults/vault-protections.md)                                       |
| **Regulatory & external risk**     | Changes in law or regulation restrict access, assets, or venues.                                                                                | [Regional Availability](../../legal/regional-availability.md) and the [Risk Warnings and Disclaimers Statement](../../legal/risk-warnings-and-disclaimers-statement.md) |

### Risk Differs by Product

**Market Neutral strategies** hedge directional price exposure and earn returns from spreads, funding rates, and volatility premia. They are designed for lower volatility — but hedging removes market direction, not risk. Their main exposures are basis divergence, funding reversals, and counterparty risk on the venues where they execute.

**Directional strategies** (CTA and momentum-based vaults) take deliberate market exposure. Drawdowns are a normal part of how these strategies operate, and returns depend on the manager's signals being right more often than wrong. Expect materially higher variance than market neutral products.

**NT Earn** aggregates USDC lending across Solana protocols. It carries no trading risk, but it is exposed to the smart contract and solvency risk of the underlying lending protocols and to falling lending rates.

**Neutral Autopilot** allocates across multiple Neutral Strategy Vaults. Diversification reduces the impact of any single strategy underperforming — but Autopilot inherits every risk of the vaults it allocates to. It diversifies strategy risk; it does not remove it.

### Liquidity & Redemption Risk

Deposits and withdrawals are batched and processed on each vault's schedule, not instantly. Some vaults have lockup periods; all have redemption periods, and some (such as [Multi-Asset Volatility Arbitrage](../market-neutral/multi-asset-volatility-arbitrage.md)) redeem quarterly with notice requirements. Between submitting a withdrawal request and receiving funds, your capital remains in the strategy and its value continues to move with performance.

Requests cannot be cancelled once submitted, and in stressed markets a strategy may need to unwind positions at worse prices to meet redemptions. The per-vault liquidity reserve is designed to absorb normal redemption flow — it is not a guarantee that every exit completes on the usual schedule in every market condition. Always check the lockup, redemption period, and any notice requirements in the vault's details tab before depositing.

### What Our Controls Do — and Don't

Audits, institutional custody, programmatic vault protections, and curator vetting exist to control operational and platform risk: they constrain where funds can move, who can act, and how fast parameters can change. What they cannot do is make a losing strategy profitable, keep an external venue solvent, or guarantee liquidity on demand. When you allocate, you are taking strategy and counterparty risk in exchange for the returns the strategy targets.

For the complete legal disclosure, read the [Risk Warnings and Disclaimers Statement](../../legal/risk-warnings-and-disclaimers-statement.md) before depositing.
