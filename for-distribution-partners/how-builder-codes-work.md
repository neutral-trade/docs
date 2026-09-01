---
description: >-
  How builder registration, first-deposit attribution, live fee tiers, accrual,
  and claims work.
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

**A builder attribution** links a user's position in one vault to a registered builder wallet. The
vault program records the link, calculates the builder's live fee share, and accrues earnings in
vault shares.

The dashboard calls the wallet address a **Builder ID**. An integration can submit that address
directly or use a human-readable builder code that resolves to it.

## The fee share

The launched program shares only the **1% annual management fee** on the 12 current strategy vaults.
It does not share performance fees.

The referred user pays exactly the same fee they would pay without a builder. The program transfers
part of the manager's collected management fee to the builder instead of adding a new charge.

The standard live ladder is documented in
[Builders Code Rebate](neutral-builders-code.md#rebate-ladder).

## Attribution is permanent, but the rate is live

Two different rules matter:

* **The builder link is permanent per user and vault.** It must be written in the user's first vault
  deposit transaction and cannot be replaced later.
* **The fee split is dynamic.** The current tier is resolved when fees are charged. Existing
  referred users move with the builder when its tier rises or falls.

Historical rate fields on an attributed-user record describe the bind event. They do not freeze or
control the live settlement rate.

## First-deposit attribution

The attributed deposit must place the following actions in one Solana transaction:

* Initialize the user's vault account when it does not exist.
* Bind the user's vault account to the builder's registered referrer account.
* Request the deposit.
* Add the NT Points attribution memo used by the rewards service.

Atomic ordering ensures that either the binding and deposit both succeed or neither does.

{% hint style="danger" %}
If the user has prior activity in that vault, an integration cannot add or change its builder
attribution. Always require successful attribution before presenting the first deposit transaction
for signature.
{% endhint %}

## Registration and tiers are per vault

A builder registers separately on every vault it distributes. Registration on one vault does not
enable attribution on another.

Each vault also maintains its own **referred net deposits** counter for that builder. Successful
referred deposits raise it and referred withdrawals lower it. The counter is measured in the
vault's deposit asset minor units and is separate from attributed TVL, which moves with share price.

The program selects the greatest tier threshold that the counter has reached. A counter below
$100,000 receives no share; a counter at exactly $100,000 receives 10%. The same rule applies at
every higher boundary.

## Effective fees and discounts

When the vault charges a user's management fee, it first applies any user-specific fee setting.
This includes an eligible VIP discount on Neutral Autopilot. The builder's live percentage is then
applied to the fee actually charged.

The vault program supports a per-builder rate override as an administrative control. If one is
configured, the effective rate shown in the dashboard and API is authoritative. Otherwise, the
standard tier schedule determines the rate.

## Earnings and claims

The builder's share accrues as **vault shares**, not as a fixed cash balance. Its token value can
rise or fall with the vault's price per share.

A claim has two stages:

* The builder signs a claim request. Accrued shares move into a pending withdrawal.
* A keeper settles the request after the vault's cooldown and processing conditions are satisfied.

The amount shown at request time is an estimate. The program calculates the final token amount at
settlement using the then-current price per share. Only settled claims appear in the payout ledger.

## Vault-level controls

The vault manager can enable or disable referrals, configure the tier schedule, set a minimum
builder deposit for registration, apply a builder-specific override, or deactivate a builder.

Deactivation prevents future binds and accrual. Earnings already accrued to the builder remain
claimable.

## Verify the state

The authoritative balances and configuration are onchain:

* The builder's referrer account contains its referred net deposits, accrued shares, override flags,
  and active status for that vault.
* The vault account contains the enabled flag, registration minimum, and tier schedule.
* Fee events record the effective referral rates used for each accrual.
* Settled claims carry Solana transaction signatures.

The [builder data API](../developers/builder-code-data.md) projects this state, and the
[IDL](../developers/#idl) lets an integrator decode it directly.

## NT Points referrals are separate

The [NT Points referral system](../getting-started/neutral-trade-points-and-referrals.md) is an
offchain rewards relationship for individual users. A points code can be applied after a deposit
and earns points rather than a management-fee share.

An attributed builder deposit also emits the points memo, so the same deposit can participate in
both systems. The points record does not create the onchain fee entitlement, and a points referral
alone does not create builder attribution.

## Continue

* [Builders Code Rebate](neutral-builders-code.md) explains the commercial ladder.
* [Builder dashboard](partner-portal.md) covers registration, reporting, keys, and claims.
* [Integration guide](integration-guide.md) shows the required attributed deposit.
* [Builder-code data](../developers/builder-code-data.md) covers reporting endpoints.

