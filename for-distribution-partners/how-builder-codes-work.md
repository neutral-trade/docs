---
description: >-
  The mechanics of the on-chain fee share — what you earn, how attribution is
  captured, and the rules that cannot be undone.
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

# How builder codes work

A builder code attributes the users you bring to Neutral Trade vaults, and pays you a share of the
fees those users generate. The whole mechanism lives in the vault program, so attribution and
payouts are verifiable on chain.

## What you earn

Your share is carved out of the **vault manager's** performance and management fee take.

**It does not increase what your users pay.** A referred user and a direct user are charged exactly
the same. Your share comes out of the manager's portion, not on top of the user's.

Rates are set per vault and can be tuned per partner by agreement. Both the performance-fee share and
the management-fee share are configured independently.

## The four rules that matter

These are properties of the program, not policy choices. None of them can be worked around after the
fact, so design your integration around them.

### 1. Attribution happens once, in the user's first transaction

A user is bound to your code in the same transaction as their **first ever deposit to that vault**.

If a user has already deposited — even once, even years ago, even a single lamport — they can never
be attributed to you on that vault. There is no retroactive linking.

This is the rule that decides whether your integration earns anything. See the
[Integration guide](integration-guide.md).

### 2. The rate is captured at the moment of binding

When a user binds, the current rate is written onto their account and stays there permanently.

A rate renegotiated later applies **only to users who bind afterwards**. Your existing cohort keeps
what they were bound at. This cuts both ways: an improved rate does not lift your existing book, and
a reduced one does not erode it.

### 3. Registration is per vault

You register separately on each vault you want to distribute. There is no global registration, and
being registered on one vault gives you nothing on another.

Some vaults require you to hold a minimum position of your own before you can register. That
threshold is published per vault, and is zero on many of them.

### 4. Earnings accrue as vault shares

Your fee share accumulates as **shares in the vault**, not as a cash balance.

Its value therefore moves with vault performance between accrual and claim — up or down. You are
economically exposed to the vault you distribute, on your own earnings, until you claim them.

## The lifecycle

```
register on a vault
      │
      ▼
user arrives with your code ──► first deposit binds them ──► rate captured
      │
      ▼
user generates performance / management fees
      │
      ▼
your share accrues as vault shares
      │
      ▼
you request a claim ──► cooldown ──► settled on chain ──► tokens received
```

## Claiming

Claiming is a two-step process, deliberately:

1. **You request.** Accrued shares move to a pending state and a cooldown begins, following the same
   redemption mechanics as a normal withdrawal from that vault — see
   [Fees + Redemption Period](../additional-info/fees-+-redemption-period.md).
2. **The vault settles it** during a later processing cycle, and transfers the tokens.

The value shown at request time is an **estimate**. The final amount is recomputed at settlement,
because the share price moves in between.

You can hold one pending claim per vault at a time.

## What a vault manager controls

| Control | Effect |
| --- | --- |
| Enable referrals | Whether the vault participates at all |
| Default rates | The standard share for that vault |
| Your rate override | A negotiated rate specific to you |
| Minimum deposit | Capital you must hold to register |
| Deactivate you | Stops future accrual on that vault |

If you are deactivated, **already-accrued earnings remain yours and stay claimable.** Only future
accrual stops.

## Verifying everything yourself

Because this lives in the vault program, you do not have to trust our reporting:

* Your accrued balances sit in your referrer account on chain.
* Settled claims carry transaction signatures.
* Your effective rates derive from the vault configuration and your referrer account.

The [API](../developers/builder-code-data.md) reports all of it, and the
[IDL](../developers/#idl) lets you decode it directly.

## What this is not

Neutral Trade also runs an
[NT Points referral programme](../getting-started/neutral-trade-points-and-referrals.md) for
individual users — a separate, off-chain system with its own codes that awards points, not fees.
Builder codes are the on-chain commercial programme for distribution partners. The two are unrelated
and do not interact.

## Next steps

* [Distributors](distributors.md) — the commercial arrangement and how to get in touch
* [Partner Portal](partner-portal.md) — sign up, claim a code, register, track earnings
* [Integration guide](integration-guide.md) — the attributed deposit, in code
* [Builder-code data](../developers/builder-code-data.md) — reading earnings programmatically
* [How They Work](../neutral-strategy-vaults/how-they-work.md) — the vaults you are distributing
