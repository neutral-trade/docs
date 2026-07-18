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

# Vault Protections

When you deposit into Neutral Strategy Vaults, several independent layers of protection govern how your capital is held, moved, and priced. This page explains each of them in plain terms.

## Your funds can only move to pre-approved places

Neither Neutral Trade nor any strategy curator can withdraw your funds to an arbitrary external wallet. Every asset movement is restricted, programmatically, to a fixed set of pre-approved addresses and programs.

Curators have API access to manage strategy execution, but no access to withdraw or move user assets.

## Redemptions don't force the strategy to unwind

Each vault maintains a liquidity reserve so that redemption requests can be processed without immediately unwinding active positions. This protects both the depositor redeeming and the depositors who remain, neither is penalised by the timing of the other's exit.

## Vault pricing is protected against manipulation

Each vault's share price (NAV) combines the assets held on-chain with the value of positions deployed to external venues, which is reported on-chain by a permissioned keeper. Every price update is bounded: it can only move within a fixed buffer around the previous value, it cannot be pushed through more often than a set minimum interval, and it can only be applied while deposits and withdrawals are paused, so no one can transact against a mid-update price. An update that falls outside the allowed range is rejected by the program and must be reviewed before it can be applied. Together these controls guard against oracle manipulation, flash-loan attacks, and erroneous pricing data affecting your position.

## Deposits and withdrawals batching

Rather than processing each transaction individually, deposits and withdrawals are collected and netted against each other on a regular processing cycle before execution. (The cadence is set per vault — see each vault's details tab.) This has two benefits: it reduces unnecessary capital movement, and it prevents MEV bots from exploiting millisecond-level differences between vault pricing and external market rates.

## Fees are hard-capped, and vault-term changes are timelocked

The smart contract enforces a hard ceiling on every fee, no matter who is managing the vault: deposit and withdrawal fees can never exceed 50%, the performance fee can never exceed 75%, and the annual management fee can never exceed 20%. Live vaults run far below these ceilings — the caps exist only as a backstop that no configuration can breach.

Beyond those ceilings, the smart contract enforces a 12-hour timelock on every material change — fee adjustments, withdrawal settings, or strategy allocations — so a change is registered on-chain and only takes effect once the delay has elapsed. Those changes are made through the vault's manager authority, held under Neutral Trade's multi-party approval process (see [Security](security.md)), so no single individual can enact them unilaterally.

## There is an emergency circuit breaker

In the event of extreme market conditions or a detected anomaly, the vault can be paused on-chain, immediately halting all new deposits and withdrawals. (The same pause mechanism is also used routinely each time the vault's price is refreshed.) While a vault is paused, open positions can be unwound and the capital returned to the vault contract. This is a last-resort protection designed to contain exposure during tail-risk events while keeping your funds within the audited vault perimeter.
