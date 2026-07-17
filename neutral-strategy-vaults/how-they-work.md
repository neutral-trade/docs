---
description: >-
  The Ultimate Strategy Execution Layer for Yield, Alpha, and Degen Plays -
  Across DeFi and CeFi.
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

# How They Work

Neutral Strategy Vaults are the infrastructure layer that connects your deposit to the strategies run by Neutral Trade and its curators. This page explains how deposits and withdrawals work, and what happens to your capital between the two.

### What Curators Can and Can't Do

You deposit on Solana. That's the only chain you interact with, no bridging, no additional wallets. Behind the scenes, the vault deploys capital to execution venues (centralised exchanges, decentralized exchanges, DeFi protocols, or all), sometimes across various chains depending on the strategy.

The vault operates within a walled garden, neither Neutral Trade nor any curator can move your funds to arbitrary external addresses. Curators, the trading teams who manage strategies within Neutral Strategy Vaults, have API access to execute trades on your behalf. They can adjust positions, rebalance, and manage the strategy. All movements are restricted to pre-approved contracts and venues. They cannot withdraw or redirect your assets.&#x20;

For a full breakdown of the protections in place: [Vault Protections](vault-protections.md).

<figure><img src="../.gitbook/assets/NT-Vault-Educational-Infographic11.png" alt=""><figcaption></figcaption></figure>

### Depositing

**1. Connect your wallet** Connect a Solana-compatible wallet. Most major wallets are supported via ReOwn.

**2. Submit a deposit request** Enter the amount you want to deposit and submit the request. A few things to be aware of:

> ⚠️ **Deposit requests cannot be cancelled once submitted.** Review the amount carefully before confirming.

> ⚠️ **If the vault has reached its TVL cap, your request will be rejected.** Check the vault's current capacity on the app before submitting.

Minimum deposit amounts vary by vault. Once a request is pending, you cannot submit another deposit or withdrawal until it is processed.

**3. Your deposit is processed and shares are issued** Deposits are batched and processed together. Once processed, your funds are deployed into the strategy and you receive vault shares representing your proportional ownership of the vault's total assets. Your share price moves with the strategy's performance from this point forward.

### While Your Capital Is Deployed

Once deployed, your capital is actively managed by the strategy. Share prices update as the strategy earns or loses. Fees are deducted periodically. Some vaults have a lockup period before you can request a withdrawal, after which there is a redemption period, these are listed in each vault's details tab in the Neutral Trade app.

### Withdrawing

**1. Submit a withdrawal request** You can request a withdrawal after any applicable lockup period has ended. There exist exceptions such as with [Multi-Asset Volatility Arbitrage](../for-capital-allocators/market-neutral/multi-asset-volatility-arbitrage.md), which has a quarterly redemption period and notice requirements. See the vaults details tab in the app for all such details.

> ⚠️ **Withdrawal requests cannot be cancelled once submitted.**

Once submitted, you cannot make another deposit or withdrawal request until this one is processed.

**2. Redemption period** After submitting, the redemption period begins. The length of this period varies by strategy and is listed in each vault's details tab in the Neutral Trade app.

**3. Funds are returned to your wallet** After the redemption period, your funds are automatically returned to your wallet, net of any applicable withdrawal fees, service fees, and commission. Your vault shares are burned, reflecting your exit from the vault.
