---
description: >-
  Register a builder wallet, monitor per-vault tiers and earnings, manage an
  integration key, and request claims.
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

# Builder dashboard

The live builder flow is self-service:

* [Builder registration](https://www.neutral.trade/builder/register) registers your wallet on the
  strategy vaults you select.
* [Builder dashboard](https://www.neutral.trade/builder) shows tier progress, attributed users,
  earnings, claims, and integration credentials.

## Builder identity

Connect the wallet that will receive the rebate. Its base58 wallet address is your **Builder ID**
and the onchain referrer identity used by every selected vault.

Wallet ownership is proved with signatures:

* Registration and claim requests are Solana transactions.
* Dashboard API-key access uses Sign-In With Solana message signatures.
* There is no password or email login in the launched builder flow.

Use a wallet you control securely and expect to retain. Earnings already accrued to an address do
not move merely because an offchain organization owner changes.

## Register on vaults

The registration page loads every active strategy vault with builder referrals enabled. Select the
vaults you plan to distribute and approve registration.

Registration remains independent per vault. One wallet approval can cover the selected batch, while
the app may pack a large batch into more than one Solana transaction.

Each vault card displays its current builder-deposit requirement. A zero requirement allows
initialization and registration in the same transaction. If a vault displays a nonzero requirement,
the builder's own deposit must be processed before registration can complete.

## Read the dashboard

The dashboard is organized around four views:

* **Overview** shows total claimable value, attributed capital, users, and a vault-by-vault
  breakdown. Each vault shows its live tier and next threshold.
* **Referred users** shows the bound cohort and its vault activity.
* **Claims** shows claimable shares, pending requests, and settled payouts.
* **Integration** shows your Builder ID, current API pattern, and API-key controls.

Tier placement uses referred net deposits per vault, not the combined dashboard total. See
[How builder codes work](how-builder-codes-work.md#registration-and-tiers-are-per-vault).

## Create an API key

The Integration view asks for one wallet message signature, creates the associated partner
organization when needed, and issues a production API key.

{% hint style="warning" %}
The plaintext key is shown once. Copy it directly into a secret manager. Never place it in browser
JavaScript, a mobile binary, logs, screenshots, or source control.
{% endhint %}

Generating a replacement key in the dashboard revokes the earlier active keys after the new key is
issued. Integrators that need an overlap window can use the direct partner key-rotation API, which
keeps the old key valid for 60 seconds. See
[Access & authentication](../developers/access-and-authentication.md).

The public deposit transaction builder does not require a key in the browser. A key is for
authenticated data reads and server-side integrations.

The [reference implementation](https://github.com/neutral-trade/builder-codes-ui-example) is a
worked example that keeps the API key in a server-side proxy for authenticated vault and position
reads.

## Request a claim

Select the vault earnings you want to claim and sign the request. The app can batch requests across
vaults into one wallet approval.

A successful request is pending, not paid. A keeper settles it later under that vault's withdrawal
conditions. The final token amount can differ from the estimate because the price per share can move
before settlement.

Only one pending builder claim can exist per vault at a time.

## Common issues

**A vault is missing from registration.** The vault is inactive, deprecated, not a supported
strategy vault, or does not currently have referrals enabled.

**Registration needs a deposit.** The vault has a nonzero builder minimum. Deposit the displayed
amount, wait for processing, and retry registration.

**A referred user is absent.** Confirm that the user's first vault deposit transaction included and
successfully applied attribution. A later deposit cannot repair a missed first deposit.

**Earnings are still zero.** Attribution occurs with the deposit request, but rebate shares accrue
only when management fees are charged.

**A claim remains pending.** Settlement follows the vault's cooldown and keeper processing cycle.
See [Fees + Redemption Period](../additional-info/fees-+-redemption-period.md).
