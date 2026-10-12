---
description: >-
  Neutral Trade gives everyone on-chain access to hedge fund grade strategies:
  market-neutral, directional, and RWA vaults run by vetted trading firms.
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

# Introduction

_Hedge fund strategies. On-chain. For everyone._

**Neutral Trade** is where anyone can allocate to the systematic strategies that professional trading firms run, and where trading firms raise on-chain capital without building a fund.

For decades, these strategies sat behind a $1M minimum, a fund subscription, and a quarterly redemption window. Neutral Trade replaces that with a stablecoin deposit into an audited smart contract. You keep on-chain proof of your position, fees settle automatically, and most vaults redeem every week.

Our team combines experience from Goldman Sachs and a top-three global hedge fund with deep expertise in DeFi protocol mechanics.

## What Is Neutral Trade?

Neutral Trade is a platform of **Neutral Strategy Vaults**. Each vault connects depositor capital to one strategy, run by Neutral Trade or by an independent trading firm (a curator) that has passed our [Curator Selection](curators/curator-selection.md) review.

* **You deposit** a stablecoin, in most vaults USDC on Solana, and receive vault shares. Neutral Autopilot also supports USDC on Ethereum through Accountable Vaults.
* **The trading firm trades.** It has execution permissions only. It cannot withdraw your funds.
* **The vault does the accounting.** Share price, per-wallet high-water marks, and fees are recorded on-chain.
* **You redeem** on the vault's published schedule.

## Allocate

Start with Autopilot if you want one managed position. Select individual strategies if you want to build your own mix.

<table data-view="cards" data-full-width="true"><thead><tr><th>Category</th><th>What it means</th><th>Risk profile</th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Neutral Autopilot</strong></td><td>One deposit, allocated across Neutral Trade's live strategies and rebalanced for you.</td><td><strong>Low - Moderate</strong></td><td><a href="for-capital-allocators/neutral-autopilot.md">neutral-autopilot.md</a></td></tr><tr><td><strong>Market Neutral</strong></td><td>Strategies that aim to earn from funding, spreads, and arbitrage, not from market direction.</td><td><strong>Low - Moderate</strong></td><td><a href="for-capital-allocators/market-neutral/">market-neutral</a></td></tr><tr><td><strong>Directional</strong></td><td>Systematic strategies that take positions from quantitative signals. They carry some correlation to the market.</td><td><strong>Moderate - High</strong></td><td><a href="for-capital-allocators/directional/">directional</a></td></tr><tr><td><strong>RWA</strong></td><td>Strategies that trade regulated traditional markets, funded with USDC.</td><td><strong>Moderate</strong></td><td><a href="for-capital-allocators/rwa/">rwa</a></td></tr><tr><td><strong>NT Earn</strong></td><td>A USDC lending optimizer across Solana money markets. No fees.</td><td><strong>Conservative</strong></td><td><a href="for-capital-allocators/nt-earn.md">nt-earn.md</a></td></tr><tr><td><strong>Neutral Tokenize</strong></td><td>Coming soon. Hold a vault position as a token in your own wallet.</td><td><strong>Follows the vault</strong></td><td><a href="neutral-tokenize/overview.md">overview.md</a></td></tr></tbody></table>

Every strategy can lose money. Read the [Risk Overview](for-capital-allocators/risk-overview/) before you deposit.

## Why Allocators Use Neutral Trade

| Topic          | Traditional access                              | Neutral Trade                                                                              |
| -------------- | ----------------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Minimum**    | Often $100K to $1M                              | 100 USDC on most strategy vaults                                                           |
| **Onboarding** | Fund subscription or an account on every venue  | A wallet and one deposit transaction                                                       |
| **Redemption** | Monthly or quarterly, with 30 to 90 days notice | Weekly or twice weekly on most vaults                                                      |
| **Fees**       | Invoiced, on NAV that the manager calculates    | Charged by the vault program. On a direct vault position, against your own high-water mark |
| **Custody**    | You trust the manager                           | Movements restricted to pre-approved addresses. Four independent audits                    |

See [How They Work](neutral-strategy-vaults/how-they-work.md), [Vault Protections](neutral-strategy-vaults/vault-protections.md), and [Security](neutral-strategy-vaults/security.md).

## Curate

Trading firms keep the strategy. Neutral Trade runs everything else: 9 integrated venues with custody through Ceffu, Copper and Fordefi MPC, collateral transfers between venues, daily NAV, per-wallet fee accounting and reporting.

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Infrastructure for Trading Firms</strong></td><td>See the infrastructure Neutral Trade runs for trading firms.</td><td><a href="curators/infrastructure-for-trading-firms.md">infrastructure-for-trading-firms.md</a></td></tr><tr><td><strong>Curator Onboarding</strong></td><td>Learn what it takes to partner with Neutral Trade, and how to get started.</td><td><a href="curators/curator-onboarding.md">curator-onboarding.md</a></td></tr></tbody></table>

## Build

Distribution partners can integrate all 12 current strategy vaults and earn up to 50% of the 1% management fee through the live [Builders Code Rebate](for-distribution-partners/neutral-builders-code.md). The [Developers](developers/) section covers the REST API, the TypeScript SDK, and the program IDL.

## Who Backs Neutral Trade

**Institutional and strategic backers**

| Backer           | Backer    | Backer         |
| ---------------- | --------- | -------------- |
| Solana Labs      | YZi Labs  | DRW Labs       |
| Skyland Ventures | BlackPine | Monke Ventures |

**Angels** from IMC Trading, Cubist, Paper Ventures, Phantom, Kamino, Jupiter, Pyth, Sanctum, and more.

**Trusted by quant and DeFi researchers:** DeFi Dad, DeFi Maestro, Kel xyz, Solar, Joe Takayama, and Wrong User.

## Trusted by Leading Solana Protocols

* Kamino: [NT USDC Max Yield](https://kamino.com/lend/B2Lgk7i468Epkwpg8YtRyWkr87GENZwsgQmX8qEjryHa)
