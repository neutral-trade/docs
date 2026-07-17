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

The price at which shares are issued and redeemed (NAV) is governed by dynamic limits on how much it can move per update. This prevents oracle manipulation, flash loan attacks, and erroneous pricing data from affecting your position. If a price update falls outside the expected range, it is held for manual verification before taking effect.

## Deposits and withdrawals batching

Rather than processing each transaction individually, deposits and withdrawals are collected and netted against each other once per day before execution. This has two benefits: it reduces unnecessary capital movement, and it prevents MEV bots from exploiting millisecond-level differences between vault pricing and external market rates.

## Changes to vault terms require advance notice

Any material change to a vault, including fee adjustments, withdrawal settings, or strategy allocations, is subject to a mandatory 24-hour timelock before taking effect.

## There is an emergency circuit breaker

In the event of extreme market conditions or a detected smart contract anomaly, an emergency function can be triggered to immediately halt new deposits and withdrawals, and recall all deployed capital back to the base vault contract. This is a last-resort protection designed to contain exposure during tail-risk events while keeping your funds within the audited vault perimeter.
