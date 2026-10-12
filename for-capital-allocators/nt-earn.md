---
description: >-
  NT Earn is a no-fee USDC lending optimizer on Solana. It allocates across
  money markets such as Kamino and Jupiter Lend and rebalances for you.
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

# NT Earn

NT Earn is a USDC lending optimizer built on Neutral Strategy Vaults infrastructure. It automatically allocates your USDC across Solana money markets. It applies risk checks first, then seeks the best yield among the markets that pass.

**No fees. Withdrawals are normally available within 1 hour.**

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/earn">https://www.neutral.trade/earn</a></td></tr></tbody></table>

_Live since August 2025._

## Key Facts

| Item                | Detail                                              |
| ------------------- | --------------------------------------------------- |
| **Deposit asset**   | USDC on Solana                                      |
| **Minimum deposit** | 10 USDC                                             |
| **Fees**            | None: no management, performance, or withdrawal fee |
| **Withdrawals**     | Normally within 1 hour                              |
| **Market exposure** | None. The vault holds USDC throughout               |

## How It Works

When you deposit USDC, NT Earn distributes it across a curated set of Solana lending markets. The allocation isn't static. The system continuously monitors borrowing demand, utilization rates, and pool depth, then rebalances toward the markets earning the most without taking on excess concentration risk.

This differs from depositing directly into a single protocol. A single-protocol deposit is fully exposed to that protocol's utilization swings and smart contract risk. NT Earn holds allocations across multiple protocols simultaneously and exits positions automatically when utilization reaches stress thresholds.

## Current Lending Markets

| Protocol       | Details                                                                                        |
| -------------- | ---------------------------------------------------------------------------------------------- |
| Kamino Finance | Neutral Trade USDC Max Yield vault: allocates across multiple isolated Kamino lending markets. |
| Jupiter Lend   | Part of the Jupiter ecosystem, powered by Fluid with unified pools.                            |

## Allocation Methodology

The allocation engine does not simply chase the highest listed APY. A market must pass the risk checks below before it can receive capital.

| Factor             | What we assess                                                    |
| ------------------ | ----------------------------------------------------------------- |
| Utilization rate   | High utilization reduces liquidity available for withdrawals      |
| Borrowing demand   | Capital only flows to pools with active borrowers                 |
| Pool depth         | Shallow pools or lender-concentrated pools create withdrawal risk |
| Supply/borrow caps | System models post-deposit impact before allocating               |
| Collateral quality | Issuer risk, credit risk, and liquidation bad debt potential      |
| Oracle quality     | Price feed reliability and manipulation resistance                |

### Allocation Logic

1. Apply the entry-blocking rules (utilization thresholds, cap limits). A market that fails is excluded.
2. Rank the eligible markets by current APY.
3. Simulate post-deposit market impact. Capital is only deployed where borrowing demand can absorb it without significantly diluting yield.
4. Allocate to the highest-ranked market up to its capacity cap, then flow remaining capital to the next one.

**Withdrawal sequencing.** When you redeem, the system exits the lowest-APY positions first, preserving your highest-yielding allocations for as long as possible.

### Automated Exit Strategy

The system monitors utilization continuously and exits positions in a graduated sequence if stress conditions develop. You don't need to monitor this yourself.

| Pressure level | Response                   |
| -------------- | -------------------------- |
| Light          | Partial position reduction |
| Medium         | Increased exit ratio       |
| Critical       | 100% immediate exit        |

New deposits are blocked entirely if any market's utilization exceeds the exit threshold. This prevents deploying fresh capital into a stressed pool.

## Risks

NT Earn holds USDC throughout and takes no directional exposure to crypto prices. However, it carries risks specific to DeFi lending:

* **Smart contract risk.** Your USDC sits in the vault program and in the lending protocols it allocates to. A bug or exploit in any of them could cause a loss.
* **Oracle risk.** Lending protocol liquidations depend on price oracles. Manipulation or failure of oracle feeds could cause bad debt in the underlying pools, affecting lender returns.
* **Liquidity risk.** In extreme market conditions, high utilization across multiple protocols simultaneously could delay withdrawals beyond the standard 1-hour window. The automated exit strategy is designed to reduce this risk, but cannot eliminate it entirely.
* **Stablecoin risk.** The vault holds USDC. A loss of the USDC peg would affect the value of your position.

See the [Risk Overview](risk-overview/) for the full picture.

## Common Questions

**What is NT Earn?**

A USDC lending optimizer on Solana. It spreads your USDC across money markets and rebalances for you.

**Does NT Earn charge fees?**

No.

**How is NT Earn different from the strategy vaults?**

NT Earn lends USDC. It does not trade. The strategy vaults, such as [Neutral Autopilot](neutral-autopilot.md), run trading strategies and target a higher return with more risk.

_Products referenced are not intended for individuals in the United States, Mainland China, Hong Kong, sanctioned, or other restricted jurisdictions. This page is for informational purposes only and does not constitute an offer, solicitation, or recommendation to buy or sell any financial instrument. Digital-asset strategies involve significant risk, including possible loss of principal. See the_ [_Risk Warnings and Disclaimers Statement_](../legal/risk-warnings-and-disclaimers-statement.md)_._
