---
description: >-
  Read live tiers, referred net deposits, accrued shares, users, flows, history,
  terms, and settled builder claims.
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

Builder reporting is served from `https://api.neutral.trade`. Exact fields and parameters are in
the [interactive OpenAPI document](https://api.neutral.trade/docs).

A valid partner API key can read any referrer address. These routes are not restricted to the owner
wallet associated with the key.

## Referrer endpoints

For a builder wallet address, use:

* `GET /v2/referrer/{address}/summary`
* `GET /v2/referrer/{address}/payouts`
* `GET /v2/referrer/{address}/history`
* `GET /v2/referrer/{address}/users`
* `GET /v2/referrer/{address}/flows`

The summary is the best first request. It groups the builder's state by vault and includes active
status, asset metadata, accrued fee shares, claimable value, pending claims, attributed users,
attributed TVL, referred net deposits, the current tier, and the next tier.

## Vault schedule discovery

`GET /v2/vaults` and `GET /v2/vault/{vaultAddress}` expose the current referral configuration
under `referral`. This includes whether referrals are enabled and the ordered `tiers` array.

Each tier has `threshold`, `mfeeBps`, and `pfeeBps`. The threshold is a raw integer in that
vault asset's minor units. Read the schedule instead of hard-coding it, even though all 12 launched
strategy vaults currently use the same commercial ladder.

## Referred net deposits and tier progress

`referredNetDeposits` is a signed integer in the vault asset's minor units. It tracks referred
deposits minus referred withdrawals in that vault since tier tracking was enabled.

It deliberately differs from `attributedTvl`:

* Referred net deposits drive tier placement and do not move with share price.
* Attributed TVL is the current mark-to-market value of the bound cohort.
* Withdrawals can make referred net deposits negative.
* Pre-existing builders without a backfill start at zero when tier tracking begins.

Use the value inside each vault summary for tier progress. Do not combine minor-unit counters from
different vault assets.

`currentTier` is null below the first threshold. Otherwise it reports the reached tier index and
live management and performance referral basis points. `nextTier` reports the next threshold and
the exact remaining net deposit amount, or null at the top.

The launched standard schedule has zero performance-fee share. The management-fee component is 10%,
20%, 30%, 40%, or 50% after the corresponding threshold.

## Current terms

`GET /v2/partner/agreements` returns the authenticated partner owner's current terms across
vaults. Important fields include:

* `registered`, `active`, and `referrerEnabled`
* `referrerMinDepositAmount`
* `effectiveMfeeBps` and `effectivePfeeBps`
* `rateOverrideFlags`

The effective fields match live fee settlement. When the relevant override flag is absent, the
program derives the rate from that vault's tier schedule and the builder's current referred net
deposits.

`defaultMfeeBps` and `defaultPfeeBps` are deprecated compatibility fields. Do not use them to
project earnings.

## Attributed users and live rates

The users endpoint returns the bound cohort, position data, first attribution time, net deposits,
and related audit fields.

Some user records retain referral rates recorded at binding. Those fields describe the historical
bind event only. They do not determine current accrual. Existing referred users use the builder's
live effective rate whenever management fees are charged.

## Earnings

Accruals are share quantities rather than fixed currency amounts. The summary separates management
and performance fee shares and converts the total to token and USD values when current asset
metadata and pricing are available.

For the launched rebate, the management-fee share is the active component. A nullable USD value
means pricing is unavailable, not that earnings are zero.

## History and partial days

Completed UTC days are returned by default. `throughDate` identifies the newest completed day.

Set `includePartial=true` to include the newest provisional day. Provisional rows carry a partial
marker, and `partialThrough` states how fresh that partial coverage is. Do not mix a partial day
with completed daily values without labeling it.

Daily history includes earnings, attributed TVL, flows, closing attributed-user count, and the
closing referred-net-deposit counter used for tier placement.

## Flows and payouts

Flows provide the deposits and withdrawals made by the attributed cohort over the requested window.
Use them for cumulative capital analysis rather than treating current TVL as lifetime referrals.

Payouts contain settled builder claims and their Solana transaction signatures. A requested claim
that has not settled appears as `pendingWithdrawal` in the summary and is not yet a payout.

## Number and freshness rules

Token amounts and shares are raw integer strings. Parse them with `BigInt`, apply the asset
decimals only for display, and never route them through a JavaScript `Number`.

HTTP 503 means projection state is temporarily unavailable or degraded. Retry and show an
unavailable state rather than rendering zero.

See [API conventions](api-conventions.md) and
[How builder codes work](../for-distribution-partners/how-builder-codes-work.md).
