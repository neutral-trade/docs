---
description: 'For fintech platforms, wallets, neobanks, exchanges, custodians, and apps'
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

# Distributors

**Distribution partners** can embed Neutral Trade's 12 current strategy vaults in their own
products and earn the live Builders Code Rebate on capital they refer.

## Commercial model

Every included vault has a 1% annual management fee. The standard builder split starts at 10% once
referred net deposits in that vault reach $100,000 and rises through 20%, 30%, 40%, and 50% tiers.

The split:

* Applies to the management fee only, not performance fees.
* Comes from the vault manager's collected fee and does not increase the user's fee.
* Uses the builder's live tier separately in each vault.
* Accrues as vault shares and is claimable through the vault program.

See [Builders Code Rebate](neutral-builders-code.md) for every threshold and a fee illustration.

## Integration model

Partners can:

* Register a builder wallet on all vaults they plan to distribute.
* Build attributed first deposits with the public REST transaction builder or TypeScript SDK.
* Embed unsigned deposit and withdrawal transactions without exposing an API key.
* Pull vault, user, tier, earnings, flow, history, and payout data with a partner API key.
* Track and claim earnings in the self-service builder dashboard.

Attribution and earnings are verifiable from Solana program state and events. The backend and
dashboard provide indexed views without replacing the onchain source of truth.

## Get started

Register at [neutral.trade/builder/register](https://www.neutral.trade/builder/register), then
follow the [integration guide](integration-guide.md).

For a supported rollout, contact [partnerships@neutral.trade](mailto:partnerships@neutral.trade),
[@NeutralTradeWill on Telegram](https://t.me/NeutralTradeWill), or the
[Neutral Trade Telegram group](https://t.me/neutraltrade).

