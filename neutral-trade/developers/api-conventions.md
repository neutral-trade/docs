---
description: >-
  Response envelopes, lossless amounts, identifiers, freshness, pagination,
  partial history, previews, and unsigned transactions.
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

# API conventions

These conventions apply to `https://api.neutral.trade`. The
[interactive OpenAPI document](https://api.neutral.trade/docs) remains authoritative for each
endpoint's exact schema and status codes.

## Response envelope

Successful reads use a `success` flag and `data`. Reads derived from Solana state also include an
`asOf` cursor:

```json
{
  "success": true,
  "data": {},
  "asOf": {
    "slot": 300000000,
    "blockTime": 1800000000
  }
}
```

`asOf` identifies the chain position reflected by the projection, not the time the HTTP request
arrived. Surface it when freshness matters.

Errors set `success` to false and provide a machine-readable error or message. Policy validation
can also return HTTP 200 with `success: true` and `validation.accepted: false`, so HTTP status
alone is not enough.

## Token amounts are lossless strings

Token amounts, share counts, price-per-share values, and tier thresholds use raw base-10 integer
strings in the relevant token's **minor units**.

```json
{
  "raw": "123450000",
  "token": "123.45",
  "usd": 123.57
}
```

Treat `raw` as canonical and parse it with `BigInt`. Apply the token's decimal count only when
rendering major units.

Do not use `Number`, `parseInt`, or `parseFloat` for the canonical amount. JavaScript numbers
lose integer precision above 2^53.

Amounts sent to transaction and preview endpoints follow the same rule. For a six-decimal token,
100 tokens is the raw string `"100000000"`.

## Nullable USD values

`usd: null` means no sufficiently fresh price was available. It does not mean the token amount is
zero.

Render null as unavailable. When an aggregate includes an unpriced component, its USD total may
also be null or omitted. Inspect the response's unpriced-asset metadata instead of assuming a
stablecoin price.

## Unavailable projections

HTTP 503 means a required projection is missing, catching up, or degraded. Show a temporarily
unavailable state and retry with backoff.

Do not turn a 503 into an empty list, zero balance, or zero earnings. Those are valid data values
with materially different meaning.

## Pagination

Paginated endpoints use opaque keyset cursors:

```http
GET /v2/referrer/{address}/payouts?limit=50
GET /v2/referrer/{address}/payouts?limit=50&cursor={nextCursor}
```

Pass `nextCursor` back verbatim. Do not decode, construct, or mutate it. A null cursor means there
is no next page.

Date-grouped endpoints keep a date together on one cursor page. Other feeds state their sort order
in OpenAPI.

## Dates and daily history

Date filters are inclusive and use UTC unless the endpoint says otherwise.

Daily series normally return completed UTC days and expose `throughDate` as the completed
watermark. Referrer history can also include the provisional current day:

```http
GET /v2/referrer/{address}/history?includePartial=true
```

A provisional row is explicitly marked partial. `partialThrough` identifies its freshness. Label
partial data in charts and do not compare it with a completed day as if both covered the same
period.

Historical or reconstructed rows can carry legacy flags. Preserve those flags in downstream
reporting.

## Identifiers

Current vault endpoints use the vault's base58 Solana account address. Numeric v1 `vaultId`
values are legacy identifiers and do not work in v2 paths.

A vault position is a share balance tracked by the program. There is no transferable per-vault
share-token mint. The deposit asset mint is a separate field on the vault record.

Builder IDs and referrer path parameters are base58 wallet addresses. Human-readable builder codes
resolve to those addresses.

## Previews

`simulate-deposit` and `simulate-withdraw` estimate outcomes from current projected state. They
do not construct transactions and are not settlement guarantees.

Deposit shares can change before keeper processing. Withdrawal value can change during cooldown.
Preview requests also cannot validate every user-specific condition.

A policy rejection can return HTTP 200 with `accepted: false`. Malformed input returns HTTP 400.

## Unsigned transaction builders

The public transaction routes are:

* `POST /v2/vault/{vaultAddress}/tx/deposit`
* `POST /v2/vault/{vaultAddress}/tx/withdraw`

An accepted response contains `transactionBase64`, `instructions[]`, `blockhash`,
`lastValidBlockHeight`, required signers, compute budget, and validation data. Signature slots are
empty.

The client must:

* Verify the returned vault, amount, instructions, and required signer.
* Ask the connected user to sign.
* Submit before `lastValidBlockHeight`.
* Request a fresh build after blockhash expiry.

For referred deposits, pass `code` or `referrer` and set `requireAttribution: true`. Confirm
`attribution.applied` before signing. See the
[integration guide](../for-distribution-partners/integration-guide.md).

The API never holds a user key and never submits the transaction.

## Processing estimates

Processing timestamps derive from the configured schedule. They are estimates rather than
commitments and can be null when timing inputs are unavailable.

Do not present an estimate as a guaranteed countdown. Show the vault's actual cooldown and
processing cadence from [Fees + Redemption Period](../additional-info/fees-+-redemption-period.md).

