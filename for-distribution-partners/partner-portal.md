---
description: >-
  Sign up, claim a builder code, register on vaults, manage API keys, and track
  earnings — all self-serve.
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

# Partner Portal

The Partner Portal is where you manage your organization: sign up, claim a builder code, register as
a builder on vaults, issue API keys, and track what you have earned.

## Signing in

You sign in by **signing a message with your wallet** — no password, no email verification.

Your wallet does double duty, and this is the most important thing to understand before you start:

{% hint style="warning" %}
**The wallet you sign up with becomes both your login and your earnings address.**

It is the identity your fee share accrues to on chain. Choose a wallet you control securely and
expect to keep — ideally a multisig or hardware wallet, not a hot wallet on a laptop.

You can rotate it later, but rotation does not move earnings you have already accrued. Those stay
with the previous wallet.
{% endhint %}

One wallet maps to exactly one organization.

## Getting set up

### 1. Create your organization

Sign in with your wallet and provide your legal entity details — legal name, and optionally
jurisdiction and registration number.

You are signed in immediately after signup, and your organization starts with KYB status
**not started**.

### 2. Issue a sandbox key and build

You can issue API keys straight away, before any verification. Start with a **sandbox** key: it reads
devnet data, so you can build and test your integration end to end against the same API surface you
will use in production.

See [Access & authentication](../developers/access-and-authentication.md) for how keys work.

### 3. Complete KYB verification

{% hint style="info" %}
**Claiming a builder code requires approved KYB.** You can sign up, issue keys, and read data before
verification — but the code, and therefore attribution and earnings, unlocks only once your
organization is approved.

Start this early. It is the step most likely to sit between you and going live.
{% endhint %}

Contact us to begin verification: [partnerships@neutral.trade](mailto:partnerships@neutral.trade) or
our [Telegram group](https://t.me/neutraltrade).

### 4. Claim your builder code

Once approved, choose a code — letters, numbers, hyphens, and underscores, up to 64 characters. Codes
are stored and returned in uppercase, and are unique across all partners, so your first choice may
already be taken.

Your code resolves to your organization's owner wallet. You can re-point or disable it at any time.

### 5. Register on the vaults you want to distribute

Registration is per vault. The portal shows every vault, whether it has referrals enabled, your
effective rates, and any minimum position required.

* On vaults with **no minimum**, registration is a single transaction.
* On vaults **with a minimum**, you deposit first, wait for that deposit to be processed in the
  vault's next cycle, then register. The portal walks you through both steps and remembers where you
  are.

### 6. Go live

Issue a **production** key, point your integration at your code, and follow the
[Integration guide](integration-guide.md) to make sure attribution actually lands.

## What the portal shows you

| Screen | Contents |
| --- | --- |
| **Earnings** | Accrued fees per vault, claimable value, attributed TVL, and how many users your code has brought in |
| **Attributed users** | Your cohort, with each user's position and the fee rate captured for them |
| **History** | Daily earnings and attributed TVL over time |
| **Vaults** | Where you are registered, your effective rates, and what is still available |
| **Payouts** | Settled claims, each linking to its on-chain transaction |
| **API keys** | Issue, rotate, and revoke keys for sandbox and production |
| **Profile** | Your legal entity details, KYB status, and owner wallet |

Everything here is also available [through the API](../developers/builder-code-data.md) if you would
rather pull it into your own dashboards.

## Claiming earnings

Claims are two-step. You request, then the vault settles during a later processing cycle and
transfers the tokens.

The value shown when you request is an **estimate** — the final amount is recomputed at settlement,
because the share price moves in between. You can hold one pending claim per vault.

See [How builder codes work](how-builder-codes-work.md#claiming), and
[Fees + Redemption Period](../additional-info/fees-+-redemption-period.md) for the cooldown and
redemption-window rules your claim follows.

## Managing API keys

* **Issue** — the plaintext key is shown **exactly once**. Store it in your secret manager
  immediately; only a hash is retained, so a lost key must be rotated rather than recovered.
* **Rotate** — issues a replacement while the old key keeps working for **60 seconds**, so you can
  deploy without downtime.
* **Revoke** — immediate, and takes effect across all API instances within 60 seconds.

Keys are environment-bound and not interchangeable. `nt_sandbox_…` reads devnet; `nt_prod_…` reads
mainnet.

## Rotating your owner wallet

If you need to move to a different wallet — a security upgrade, a change of custody — you can rotate
it yourself. Rotation is authorized by signing with the **incoming** wallet, so you must control it
first.

Three consequences to understand before you do it:

1. **Earnings already accrued stay with the previous wallet.** Rotation moves your login and your
   future accrual, not your history. Claim what you can before rotating.
2. **You will need to sign in again** with the new wallet. The old session stops working immediately.
3. **Your API keys survive.** Your organization identity is preserved, so keys and audit history
   carry over.

## Troubleshooting

| Situation | What it means |
| --- | --- |
| "This organization needs an owner wallet" | An older organization record with no wallet attached. Contact us to claim it. |
| Code claim rejected | Either the code is taken, or your KYB is not yet approved. |
| Signature rejected or expired | Sign-in challenges expire after five minutes and are single-use. Start again. |
| Earnings show zero after users deposited | Fees accrue when they are charged, not at deposit. Check that your users were actually attributed — see the [Integration guide](integration-guide.md). |
| "Data temporarily unavailable" | A freshness state, not an error. Retry shortly. |
