---
description: >-
  Earnings, attributed users, payouts, and terms for a registered builder code —
  and why these endpoints stay closed without one.
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

# Builder-code data

Served from `https://api.neutral.trade` under `/v2/referrer/…`. Exact fields and parameters are in
the interactive spec at [`api.neutral.trade/docs`](https://api.neutral.trade/docs).

{% hint style="info" %}
**These endpoints require more than a valid API key.** They are addressed by referrer wallet, and
your key authorizes exactly one: the owner wallet of your organization. If you are not a distribution
partner, this section does not apply to you — nothing else in the API is affected.

See [Access & authentication](access-and-authentication.md), and
[How builder codes work](../for-distribution-partners/how-builder-codes-work.md) for the
program itself.
{% endhint %}

## What you can read

| Group | What it gives you |
| --- | --- |
| **Summary** | Accrued fees per vault, claimable value, attributed TVL, attributed user count, and any pending withdrawal |
| **Attributed users** | The cohort your code brought in: shares, net deposits, first deposit time, and the fee rate captured for each |
| **Flows** | Deposits and withdrawals made by your attributed users over a window |
| **Daily history** | Earnings, attributed TVL, and flows as a completed-day series |
| **Payouts** | Settled claims, each with a transaction signature you can verify on an explorer |
| **Terms** | Your current on-chain referral terms per vault |

## Your terms are chain state, not a contract record

The terms endpoint does not read a stored agreement. There is no stored agreement. It reads the
vault's on-chain referral configuration and any override applied to your referrer account, then
resolves them exactly as the program does.

Each vault returns:

| Field | Meaning |
| --- | --- |
| `registered` | You hold a referrer account on this vault |
| `active` | The vault manager has not disabled you |
| `referrerEnabled` | The vault has referrals switched on at all |
| `defaultPfeeBps` / `defaultMfeeBps` | The vault's standard referral rates |
| `effectivePfeeBps` / `effectiveMfeeBps` | **What you actually earn** — the numbers to display |
| `rateOverrideFlags` | Which fees carry a negotiated override |
| `referrerMinDepositAmount` | Capital required to register on this vault |

Because this is chain state, it is verifiable independently. Anything we report here can be checked
against the program.

{% hint style="warning" %}
**Effective rates apply to users who bind from now on.** The program captures a user's rate at the
moment they are attributed, and that user keeps it permanently. A renegotiated rate does not apply
retroactively to your existing cohort.

Attributed-user records carry each user's own captured rate. Use those to explain historical
earnings; use the terms endpoint to project future ones.
{% endhint %}

## Reading earnings correctly

**Accruals are share counts, not currency.** Your earnings accumulate as vault shares, so their value
moves with vault performance until you claim. The summary converts to token and USD for display, but
the share count is the underlying quantity.

**Everything follows the standard number rules** in [API conventions](api-conventions.md): raw
integer strings, `BigInt` only, nullable USD meaning "no price" rather than zero.

**Daily history contains completed UTC days only.** Today is never included. Each response carries a
watermark showing the newest day covered — show it, or partners will report earnings as missing when
the day simply has not closed.

**Attributed TVL is your cohort's current position value**, not the total you have ever referred.
Users who withdraw leave it. Track cumulative contribution through flows instead.

## Payouts

The payout ledger records claims that have **settled on chain**, each with a transaction signature.
A claim you have requested but that has not yet settled appears as a pending withdrawal on the
summary, not as a payout.

This distinction matters when reconciling: pending is a promise, a payout is money that moved.

## Failure modes specific to these endpoints

| Response | Cause |
| --- | --- |
| `403` | The address you requested is not the one your key authorizes |
| `403` with `OWNER_WALLET_REQUIRED` | Your organization has no owner wallet — claim one in the portal |
| Empty results, `200` | You are registered but have no attributed users yet, or none have generated fees |
| `503` | Projection unavailable or degraded — retry; do not render zeros |

An empty result and a `503` mean different things. The first says "nothing yet", the second says "we
do not currently know". Never collapse them into the same UI state.

## Verifying independently

Every figure here derives from on-chain events. If you want to check our numbers:

* Your referrer account holds the authoritative accrued balances.
* Settled payouts carry transaction signatures.
* Your effective rates come from the vault configuration and your referrer account.

The [IDL](./#idl) lets you decode all of it directly.
