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

One code carries two rewards:

* **NT Points** — always on. You earn **10% of the NT Points** your referees earn. Nothing to activate.
* **Revenue share** — off until you turn it on. Once activated, the same referral also pays you a share of the **management fee** the vault charges your referees. They pay nothing extra.

→ View your referrals: [https://www.neutral.trade/referrals](https://www.neutral.trade/referrals)

### NT Points from referrals

Referral-based NT Points are included in **daily TVL point distributions**:

* Each day, the system snapshots total TVL (including referee deposits).
* Points are distributed alongside all other daily rewards.

Rules and validations:

* Users **cannot refer themselves**.
* Each user can **apply one** referral code only. Once applied, it does not change.
* Referral codes can be applied **any time**, even after a user has already deposited.
* Invalid or duplicate codes trigger a simple error notification.

### Revenue share

Revenue share is no longer limited to distribution partners. **Any wallet can activate it.** It uses the same onchain program and the same ladder that pays registered builders: your share is carved out of the vault manager's **1% annual management fee**, and the referred user's fee does not change.

It is **off until you turn it on**. Activating takes one signature to mint your code, then one onchain transaction to register on the vaults you want — see [Referral Revenue Share](referral-revenue-share.md) for the full walkthrough, the ladder, and claims.

Turn it on **before** you share your link. Fee attribution is written into a referee's first deposit on a vault, so a deposit that lands while you are unregistered earns you points only, and that vault cannot be backfilled for that user.

#### One referrer per user

When a referee deposits through neutral.trade, the fee attribution follows **their existing NT Points referrer** — not whatever code the URL happened to carry. Points and revenue share therefore always name the same person.

One consequence: if a referee's points referrer has never activated revenue share on that vault, the deposit simply carries no revenue share. It does not fall through to whoever's link was clicked most recently.

Deposits made inside a distribution partner's own app follow a different path — that app writes the onchain referrer itself, so the fee can go to the partner while the points stay with the user's original referrer. See [How Builder Codes Work](../for-distribution-partners/how-builder-codes-work.md).

## How the two rewards differ

Both rewards travel on the same code, but they are recorded in different places and follow different rules.

| | NT Points referral | Revenue share |
| --- | --- | --- |
| Where it lives | Offchain rewards record | Onchain, in the vault program |
| Scope | One referrer per wallet, all vaults | Per vault |
| When it is set | Any time, including after a deposit | The referee's first deposit on that vault |
| Can it be added later | Yes | No |
| Activation needed | None | Register on each vault |
| Pays | 10% of the referee's NT Points | A tiered share of the management fee |

Applying a points code after the fact still earns points, but it cannot create or repair a missing fee attribution.

See [Builders Code Rebate](../for-distribution-partners/neutral-builders-code.md) and [How builder codes work](../for-distribution-partners/how-builder-codes-work.md) for the onchain mechanics in full.
