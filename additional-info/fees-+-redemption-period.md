---
description: >-
  The 1% management fee across the 12 current strategy vaults, performance fees,
  builder rebates, and the weekly redemption schedule.
---

# Fees + Redemption Period

All 12 current Neutral Strategy Vaults have a **1% annual management fee** as their base schedule. The management fee accrues over elapsed time and is charged in vault shares.

At a simple annualized rate, 1% is approximately 0.00274% per day. Actual charges use the program's elapsed-time calculation and current user-specific fee setting rather than a rounded daily rate.

A disclosed promotion, VIP discount, or wallet-level fee setting can reduce the management fee actually charged. It does not change the vault's 1% base schedule.

The production VIP Program currently applies to Neutral Autopilot. Its Silver, Gold, and Diamond tiers reduce the standard 1% annual management fee to 0.90%, 0.80%, and 0.70%, respectively. Performance fees are not discounted.

## Builder fee split

The Builders Code Rebate shares part of the management fee with an attributed builder:

* The user-specific management fee is calculated first.
* The builder receives its live per-vault tier percentage of that charged fee.
* The split comes from the manager's fee and does not increase the user's cost.
* Performance fees are excluded from the launched builder ladder.

## Performance fee

Some vaults also charge a **performance fee**. It applies only to profit above the user's high-water mark and varies by vault.

If a position has not made a new post-fee profit above its high-water mark, no performance fee is charged for that interval.

The high-water mark is the user's highest post-fee position value used for performance-fee accounting. A new deposit can adjust the account's weighted entry basis according to the vault program rules.

## Position values

**Balance** is the current value of the user's vault shares after charged fees.

**Earnings** is the user's profit shown after management and performance fees.

**Performance fee paid** is the cumulative performance fee charged on profit above the high-water mark.

## Withdrawals

From 12 October 2026, Neutral Strategy Vaults follow a fixed weekly redemption schedule. Each vault is on one of three schedules: Autopilot, once-weekly, or twice-weekly.

You can submit a withdrawal request on any day. The request joins the next cutoff, and the vault redeems it on the redemption day for that cutoff. Every cutoff is at 00:00 UTC, the start of the day.

![Redemption schedule for Autopilot, once-weekly, and twice-weekly vaults](https://1924233991-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F6YjCIQB3ardoMeqGMIF8%2Fuploads%2Ffw547BvNapWdcjmCR8I4%2Fredemption-schedule.jpg?alt=media)

### Redemption schedule

| Schedule     | Request window      | Cutoff (UTC)  | Redemption day            |
| ------------ | ------------------- | ------------- | ------------------------- |
| Autopilot    | Monday to Sunday    | Monday 00:00  | Saturday after the cutoff |
| Once-weekly  | Tuesday to Monday   | Tuesday 00:00 | Friday after the cutoff   |
| Twice-weekly | Tuesday to Thursday | Friday 00:00  | Monday after the cutoff   |
| Twice-weekly | Friday to Monday    | Tuesday 00:00 | Friday after the cutoff   |

A request made on the cutoff day itself falls into the next window. For example, a once-weekly request made on Monday is redeemed that Friday, and a request made on Tuesday is redeemed on Friday of the next week.

### Vaults on each schedule

**Autopilot (Saturday redemptions)**

* Neutral Autopilot

**Once-weekly (Friday redemptions)**

* Mid-frequency Market Making
* CTA - Adaptive Alpha
* HFT Multi-factor
* CTA - Longshort Alpha
* CTA - Systematic Alpha

**Twice-weekly (Monday and Friday redemptions)**

* Delta Neutral Arbitrage
* Hyperliquid Funding Arb
* Options Market Making

**Exceptions**

NT Earn, Multi-Asset Volatility Arbitrage, and Meridian Liquidity Provider do not follow this schedule. They keep their own redemption terms, shown in each vault's Details view.

### Until settlement

The user remains exposed to changes in the vault's price per share until settlement. The value shown when a withdrawal or builder claim is requested is therefore an estimate rather than a fixed redemption amount.

Each vault's Details view contains its current minimums, lock, redemption schedule, management fee, and performance fee.
