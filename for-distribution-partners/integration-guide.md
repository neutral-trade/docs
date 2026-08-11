---
description: >-
  Making attribution land — the one-transaction attributed deposit, and the
  mistakes that silently cost you every user.
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

# Integration guide

This page covers the part of a distribution integration that actually earns you money: making sure
the users you send are attributed to your builder code.

{% hint style="danger" %}
**Attribution is one-shot and cannot be repaired.**

A user is bound to your code in the same transaction as their **first ever deposit to that vault**.
If that transaction lands without the binding, that user can never be attributed to you on that
vault — not by a support ticket, not by a backfill, not by us.

Get this right before you drive traffic.
{% endhint %}

## The shape of it

The SDK builds a single transaction that opens the user's vault account, binds them to your code, and
submits their deposit together:

```ts
import { buildAttributedDepositTx } from "@neutral-trade/sdk";

const tx = await buildAttributedDepositTx({
  code: "ACME",
  resolveCode,        // see below
  user,               // the user's wallet signer
  vault,              // vault address
  amount,             // raw integer, smallest unit — bigint
});
```

All three actions are in one transaction on purpose. They either all land or none do, so there is no
window where a deposit succeeds unattributed.

## Resolving your code in the browser

`resolveCode` turns your human-readable code into the on-chain address it points to. Point it at the
public resolver:

```
GET https://api.neutral.trade/public/codes/ACME
→ { "success": true, "data": { "code": "ACME", "referrer": "<base58 address>" } }
```

This endpoint is **public and CORS-enabled deliberately** so it can be called from your frontend.

{% hint style="warning" %}
**This is the only Neutral endpoint your browser code should call.** Your API key belongs on your
server. A key in a browser bundle is a leaked key.
{% endhint %}

Cache the resolution for at most 60 seconds. Codes can be re-pointed, and a stale cache attributes
users to the wrong address.

## Amounts

`amount` is a **raw integer in the asset's smallest unit** — not a UI decimal. For a 6-decimal
stablecoin, 100 tokens is `100_000_000n`.

Use `BigInt` throughout. Converting through `Number` loses precision on large balances and produces
a deposit that does not match what the user entered.

## Checking before you build

Before showing a user a deposit flow, confirm the vault will actually attribute them:

* **Is the vault referral-enabled, and are you registered and active on it?** Read your
  [terms](../developers/builder-code-data.md#your-terms-are-chain-state-not-a-contract-record) per
  vault. If you are not registered there, deposits earn you nothing.
* **Has this user deposited to this vault before?** If so, attribution is impossible. Decide whether
  to show them the vault anyway — usually yes, since they are still your user — but do not expect
  earnings.

## Testing it end to end

Do this on devnet with a sandbox key before you go live:

1. Register on a devnet vault.
2. Run a fresh wallet through your real deposit flow.
3. Wait for the vault's next processing cycle — attribution binds immediately, but fees accrue only
   when charged.
4. Confirm the wallet appears in your attributed users.

**Step 4 is the test.** A transaction that succeeds proves nothing about attribution; only the cohort
appearing confirms it. Verify with a wallet that has never touched that vault, since a reused test
wallet will silently fail to bind and look identical to a bug in your integration.

## The failure that looks like success

The most expensive mistake in this integration is not an error. It is a deposit flow that works
perfectly, transactions that confirm, users who are happy — and no attribution, because the binding
was never in the transaction.

Nothing surfaces this except checking your cohort. Build the check into your launch, and monitor
attributed user count against your own signup numbers afterwards. A growing gap means attribution is
silently failing.

## Rates

The rate a user is bound at is **captured permanently** at that moment. Your negotiated rate applies
to users who bind from that point on; your existing cohort keeps what they had.

Attributed-user records carry each user's own captured rate, which is what explains historical
earnings. See [How builder codes work](how-builder-codes-work.md#2-the-rate-is-captured-at-the-moment-of-binding).

## Reading your earnings

Pull them into your own systems through the API — see
[Builder-code data](../developers/builder-code-data.md). Two rules worth repeating:

* Amounts are raw integer strings. `BigInt` only.
* A `null` USD value means "no price available", not zero. A `503` means "temporarily unavailable",
  not "you earned nothing". Neither should render as `$0.00`.

## Checklist before launch

- [ ] Registered and active on every vault you will offer
- [ ] Code resolves through the public endpoint from your frontend
- [ ] API key is server-side only, and absent from your client bundle
- [ ] Amounts handled as `BigInt` end to end
- [ ] A fresh test wallet completed a deposit **and appeared in your attributed users**
- [ ] Users who already hold a position are handled without breaking
- [ ] Monitoring in place comparing attributed users against your own signups

## Getting help

[@NeutralTradeWill on Telegram](https://t.me/NeutralTradeWill), or our
[Telegram group](https://t.me/neutraltrade).
