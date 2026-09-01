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

# Neutral Trade Points & Referrals

<figure><img src="../.gitbook/assets/season2.jpg" alt=""><figcaption></figcaption></figure>

_Season 2 is the current active rewards period._

## NT Points

**NT Points** track your contribution to the Neutral Trade protocol. The more capital you deposit and the longer you keep it working in Neutral Strategy Vaults, the more points you accumulate.

**The goal of NT Points is simple:**

Align user incentives with protocol growth. Reward those who provide liquidity and support Neutral Trade's sustainable scaling.

NT Points track your cumulative contribution to the protocol. Your total across all seasons also provides one qualification path for the [Neutral VIP Program](neutral-vip-program.md) on Neutral Autopilot.

→ View your points balance: [neutral.trade/points](https://www.neutral.trade/points)

### How You Earn NT Points

There are two ways points accrue, both run simultaneously.

**1. Deposit points (daily)**

Every day you have funds in a Neutral Strategy Vault, you earn points based on your deposit size, adjusted by that vault's multiplier.

Larger deposit × longer duration × higher-multiplier vault = more points.

**2. Fee points (monthly)**

When your vault activity generates fees, you earn an additional allocation of points based on your share of total protocol fees that month. These are calculated at month-end and distributed daily over the following month.

This means active depositors in higher-performing vaults earn points from two sources simultaneously.

## NT Points and Neutral VIP

The VIP points path combines your total NT Points across all seasons with a minimum **$10,000 balance in Neutral Autopilot**:

| Tier    | Total NT Points | Minimum Autopilot balance | Management fee discount |
| ------- | --------------- | ------------------------- | ----------------------- |
| Silver  | 20,000          | $10,000                   | 10% off                 |
| Gold    | 60,000          | $10,000                   | 20% off                 |
| Diamond | 200,000         | $10,000                   | 30% off                 |

Both the points threshold and the $10,000 Autopilot balance are required on this path. A separate direct-balance path can qualify without points at $100,000 for Silver, $1 million for Gold, or $3 million for Diamond. Reaching a threshold makes the wallet eligible; the user must still claim the tier in the app before its fee discount is processed.

See [Neutral VIP Program](neutral-vip-program.md) for the full qualification, claim, and maintenance rules.

## Referrals

When someone joins using your code, they become your **referee**, and you are registered as their **referrer**.

Referrers earn **10% of the NT Points** earned by the users they refer.

→ View your referrals: [https://www.neutral.trade/referrals](https://www.neutral.trade/referrals)

### Distribution Schedule

Referral-based NT Points are included in **daily TVL point distributions**:

* Each day, the system snapshots total TVL (including referee deposits).
* Points are distributed alongside all other daily rewards.

### Rules & Validations

* Users **cannot refer themselves**.
* Each user can **apply one** referral code only, once applied, it’s permanent.
* Referral codes can be applied **any time**, even after a user has already deposited.
* Invalid or duplicate codes trigger a simple error notification.

## Points referrals and builder attribution

**NT Points referrals** and the **Builders Code Rebate** are separate mechanisms:

* A points referral is an offchain, user-level rewards relationship. It can be applied after a user has deposited and pays 10% of the referee's NT Points to the referrer.
* Builder attribution is an onchain, per-vault commercial fee relationship. It must be included in the user's first deposit transaction for that vault and shares the management fee with a registered builder.

An attributed builder deposit also includes the NT Points attribution memo, so one first deposit can participate in both systems. A points referral by itself does not create a management-fee rebate, and applying a points code later cannot repair missing builder attribution.

See [Builders Code Rebate](../for-distribution-partners/neutral-builders-code.md) and [How builder codes work](../for-distribution-partners/how-builder-codes-work.md).
