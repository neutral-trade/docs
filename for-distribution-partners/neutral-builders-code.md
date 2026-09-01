---
description: >-
  The live management-fee rebate for builders who refer capital to Neutral
  Trade's 12 strategy vaults.
---

# Builders Code Rebate

**The Builders Code Rebate** is live from 1 September 2026. A builder earns a share of the
management fee charged to users it refers. The referral share comes from the vault manager's fee
and never adds a fee for the referred user.

The program is enabled across all 12 current Neutral Strategy Vaults. Each has a **1% annual
management fee** before any user-specific promotion or VIP discount. Performance fees are not part
of the Builders Code Rebate.

## Rebate ladder

The standard management-fee split is:

* Below $100,000: 0%
* $100,000 to below $500,000: 10%
* $500,000 to below $3,000,000: 20%
* $3,000,000 to below $5,000,000: 30%
* $5,000,000 to below $10,000,000: 40%
* $10,000,000 and above: 50%

Thresholds are inclusive at the lower bound. A builder reaches the 20% tier at exactly $500,000,
for example.

## How tier placement works

**Referred net deposits** are the referred deposits into one vault minus referred withdrawals from
that vault. They are not the current market value of the referred positions.

The ladder is evaluated separately for every vault:

* Capital referred to different vaults is not pooled for tier placement.
* Moving above a threshold raises the live split for that vault.
* Withdrawals can move the builder back to a lower tier.
* The live tier applies to the whole attributed cohort when management fees are charged. The rate is
  not frozen when a user is first attributed.
* Below the first threshold, attribution still remains in place and the builder can qualify later.

For example, $400,000 of referred net deposits in each of two vaults produces a 10% split in each
vault. It does not combine into an $800,000 book and a 20% split.

## What the rebate is worth

The builder receives its tier percentage of the management fee actually charged:

```
management fee charged = fee base × effective user management-fee rate × elapsed time
builder rebate         = management fee charged × live builder split
```

Suppose a builder has $600,000 of referred net deposits in one vault, placing it in the 20% tier.
If the same $600,000 remains subject to the full 1% management fee for a full year, the annualized
management fee is $6,000. The builder accrues $1,200 and the manager retains $4,800.

The fee accrues over time, so this is an annualized illustration rather than a guaranteed payment.
The builder's earnings accrue as vault shares, whose value can move before a claim settles.

## Promotions and VIP discounts

A user-specific fee reduction is applied before the builder split. This includes any eligible
[Neutral VIP Program](../additional-info/neutral-vip-program.md) discount on Neutral Autopilot.

If a referred user has a 20% discount on the 1% management fee, the effective management-fee rate is
0.8%. The builder then receives its live tier percentage of the reduced amount. Referred users
never pay more because a builder is attached.

## Included vaults

The launch covers all 12 configured strategy vaults. The builder registration picker reads
participation from each vault's live onchain `referrerEnabled` setting, so it remains the
authoritative list as the catalog changes.

Registration and tier progress are maintained independently for every included vault.

## Start building

Connect the wallet that will receive earnings at
[neutral.trade/builder/register](https://www.neutral.trade/builder/register), select the vaults you
want to distribute, and register. That wallet address becomes your **Builder ID**.

Use the [builder dashboard](partner-portal.md) to track tiers, referred users, earnings, and claims.
Use the [integration guide](integration-guide.md) before sending users into a deposit flow because
attribution must be included in their first vault deposit transaction.
