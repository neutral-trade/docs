---
description: >-
  Build a first deposit that requires builder attribution, using the public
  transaction API or the TypeScript SDK.
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

Builder attribution must be applied in the user's first deposit transaction for each vault. The
recommended integration rejects an unattributed build instead of quietly allowing the deposit to
continue.

{% hint style="danger" %}
A successful deposit is not proof of attribution. Require an affirmative attribution result before
asking the user to sign. If the first deposit lands without the binding, it cannot be added later.
{% endhint %}

## Public transaction API

The public builder returns an unsigned Solana v0 transaction. It is CORS-enabled and metered by IP,
so a frontend does not need an API key.

```ts
const response = await fetch(
  `https://api.neutral.trade/v2/vault/${vaultAddress}/tx/deposit`,
  {
    method: "POST",
    headers: { "content-type": "application/json" },
    body: JSON.stringify({
      userAddress,
      amountRaw: "100000000",
      referrer: builderId,
      requireAttribution: true,
    }),
  },
);

const payload = await response.json();

if (
  payload.success !== true ||
  payload.data?.validation?.accepted !== true ||
  payload.data?.attribution?.applied !== true ||
  typeof payload.data?.transactionBase64 !== "string"
) {
  throw new Error("Builder attribution was not applied");
}

const transactionBase64 = payload.data.transactionBase64;
```

`vaultAddress` is the base58 vault account, `builderId` is the builder wallet address, and
`amountRaw` is a base-10 string in the deposit token's minor units. For a six-decimal asset,
100 tokens is `"100000000"`.

Use exactly one of:

* `referrer: builderId` to attribute directly to a registered builder wallet.
* `code: "ACME"` to let the API resolve a human-readable builder code.

`requireAttribution: true` is essential for a referral flow. Without it, attribution can soft-fail
and the API can still return a valid unattributed deposit transaction. In strict mode, any
attribution failure returns HTTP 200 with `validation.accepted: false`, an
`ATTRIBUTION_REQUIRED` rejection, and no transaction.

Deserialize `transactionBase64`, verify the vault, amount, instructions, and required signer, then
ask the connected user wallet to sign and submit before `lastValidBlockHeight`. Request a fresh
build after expiry. The API never signs or submits for the user.

## TypeScript SDK

The SDK builder returns the ordered instructions that your application must place in one
transaction:

```ts
import { address, createSolanaRpc } from "@solana/kit";
import { buildAttributedDepositTx } from "@neutral-trade/sdk";

const rpc = createSolanaRpc(rpcUrl);

const instructions = await buildAttributedDepositTx(rpc, {
  user,
  vault: address(vaultAddress),
  amount: 100_000_000n,
  referrer: address(builderId),
});
```

`user` is the user's `TransactionSigner`. `amount` is a `bigint` in token minor units. The
builder verifies the vault, builder registration, builder minimum, user eligibility, and deposit
minimum before returning instructions.

For a human-readable code, supply `code` and a `resolveCode` function instead of `referrer`.
The public resolver is:

```http
GET https://api.neutral.trade/public/codes/ACME
```

Cache a code resolution for no more than 60 seconds because a code can be repointed or disabled.

## What one attributed deposit contains

The REST and SDK paths construct the same atomic ordering:

* Initialize the user's vault account when needed.
* Bind it to the registered builder.
* Request the deposit.
* Add the NT Points attribution memo.

All instructions must stay in the same transaction and in the returned order.

## Eligibility checks

Attribution succeeds only when:

* The vault has builder referrals enabled.
* The builder is registered and active on that vault.
* The builder satisfies any vault-level registration deposit requirement.
* The user is not the builder.
* The user's vault account has no prior activity.
* The deposit meets the vault minimum and passes current vault policy.

Use a fresh wallet for end-to-end testing. A reused test wallet can correctly reject attribution
even when the integration is implemented properly.

## Confirm and monitor

After submission:

* Confirm that the transaction finalized.
* Confirm `attribution.applied` was true in the build response.
* Confirm the user appears under Referred users or
  `GET /v2/referrer/{builderId}/users`.
* Compare attributed-user growth with your own completed first-deposit count.

The rate displayed on an attributed-user record is not a permanent settlement rate. Earnings use
the builder's live per-vault tier or configured override when management fees are charged.

## Launch checklist

- [ ] Registered and active on every vault offered
- [ ] Builder ID or code resolves to the intended wallet
- [ ] `requireAttribution: true` set on every referred first deposit
- [ ] No API key shipped in the frontend
- [ ] Amounts handled as integer strings or `bigint`, never floating-point numbers
- [ ] Unsigned transaction inspected before wallet signing
- [ ] Fresh-wallet test finalized and appeared in Referred users
- [ ] Attribution monitoring compared with completed first deposits

Exact request and response schemas remain available at
[api.neutral.trade/docs](https://api.neutral.trade/docs).
