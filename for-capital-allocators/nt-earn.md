---
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
---

# NT Earn

NT Earn is a USDC lending aggregator built on Neutral Strategy Vaults infrastructure. It automatically allocates your USDC across Solana's leading lending protocols, optimizing for risk-adjusted yield rather than raw APY.

**No fees. Withdrawals available within 1 hour.**

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/earn">https://www.neutral.trade/earn</a></td></tr></tbody></table>

_Live since August 2025._

## How it works

When you deposit USDC, NT Earn distributes it across a curated set of Solana lending markets. The allocation isn't static, the system continuously monitors borrowing demand, utilization rates, and pool depth, then rebalances toward the markets earning the most without taking on excess concentration risk.

This differs from depositing directly into a single protocol. A single-protocol deposit is fully exposed to that protocol's utilization swings and smart contract risk. NT Earn holds allocations across multiple protocols simultaneously and exits positions automatically when utilization reaches stress thresholds.

## Current lending markets

| Protocol       | Details                                                                                        |
| -------------- | ---------------------------------------------------------------------------------------------- |
| Kamino Finance | Neutral Trade USDC Max Yield vault: allocates across multiple isolated Kamino lending markets. |
| Jupiter Lend   | Part of the Jupiter ecosystem, powered by Fluid with unified pools.                            |

## Allocation methodology

Rather than chasing the highest listed APY, the allocation engine weighs multiple factors before deploying capital.

**Protocol and market selection criteria:**

| Factor             | What we assess                                                    |
| ------------------ | ----------------------------------------------------------------- |
| Utilization rate   | High utilization reduces liquidity available for withdrawals      |
| Borrowing demand   | Capital only flows to pools with active borrowers                 |
| Pool depth         | Shallow pools or lender-concentrated pools create withdrawal risk |
| Supply/borrow caps | System models post-deposit impact before allocating               |
| Collateral quality | Issuer risk, credit risk, and liquidation bad debt potential      |
| Oracle quality     | Price feed reliability and manipulation resistance                |

### **Allocation logic:**

1. Rank available markets by current APY
2. Check entry-blocking rules (utilization thresholds, cap limits)
3. Simulate post-deposit market impact, capital is only deployed where borrowing demand can absorb it without significantly diluting yield
4. Allocate to the highest-APY market up to its capacity cap, then flow remaining capital to the next highest

**Withdrawal sequencing:** When you redeem, the system exits the lowest-APY positions first, preserving your highest-yielding allocations for as long as possible.

### Automated exit strategy

The system monitors utilization continuously and exits positions in a graduated sequence if stress conditions develop, you don't need to monitor this yourself.

| Pressure level | Response                   |
| -------------- | -------------------------- |
| Light          | Partial position reduction |
| Medium         | Increased exit ratio       |
| Critical       | 100% immediate exit        |

New deposits are blocked entirely if any market's utilization exceeds the exit threshold. This prevents deploying fresh capital into a stressed pool.

## Risks

NT Earn holds USDC throughout and takes no directional exposure to crypto prices. However, it carries risks specific to DeFi lending:

**Smart contract risk**

**Oracle risk** — Lending protocol liquidations depend on price oracles. Manipulation or failure of oracle feeds could cause bad debt in the underlying pools, affecting lender returns.

**Liquidity risk** — In extreme market conditions, high utilization across multiple protocols simultaneously could delay withdrawals beyond the standard 1-hour window. The automated exit strategy is designed to reduce this risk, but cannot eliminate it entirely.
