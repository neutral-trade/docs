---
description: >-
  Response shape, number handling, freshness, pagination, and the failure modes
  that cost integrations real money.
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

These rules apply across every endpoint on `https://api.neutral.trade`. Two of them — number
handling and the meaning of `503` — are the ones that cause real bugs. Read those even if you skip
the rest.

Exact fields, parameters, and status codes for any individual endpoint are in the interactive spec
at [`api.neutral.trade/docs`](https://api.neutral.trade/docs), generated from the running service.

## Response envelope

Every response carries a `success` flag and a `data` object. Reads that reflect chain state also
carry `asOf`:

```json
{
  "success": true,
  "data": { },
  "asOf": { "slot": 300000000, "blockTime": 1800000000 }
}
```

`asOf` is the chain position the data was derived from — not the time you made the request. Use it
to show freshness and to detect a stalled feed.

Errors invert the flag:

```json
{
  "success": false,
  "error": "Unauthorized",
  "message": "Valid API key required."
}
```

## ⚠️ Token amounts are strings, and must stay that way

Every token amount, share count, and price-per-share is returned as a **raw integer string in the
asset's smallest unit** — not a decimal, not a JSON number.

```json
{ "raw": "123450000", "token": "123.45", "usd": 123.57 }
```

* `raw` — the canonical integer. Parse with `BigInt`, never `Number`.
* `token` — an exact decimal rendering, provided for display.
* `usd` — a floating-point convenience value, **nullable** (see below).

Passing `raw` through `Number()` or `parseFloat()` silently loses precision above 2⁵³. On a
nine-decimal asset that threshold arrives at around nine million tokens. **This is the single most
common integration bug, and it under-reports balances.**

Amounts you send follow the same rule. Preview endpoints take `amount` and `shares` as raw
minor-unit integers, not UI decimals.

## ⚠️ Null USD means "no price", not "zero"

USD fields are nullable. `null` means no non-stale price tick was available for that asset at that
chain position — it does **not** mean the value is zero.

Render `null` as `—` or "unavailable". Rendering `$0.00` tells your user they hold nothing, which is
a materially different and incorrect claim.

Where a response aggregates several assets, the USD total is **omitted entirely** if any component
lacks a price, and the unpriced assets are listed explicitly. We never substitute a fallback price,
and there is no `$1.00` assumption for stablecoins.

## ⚠️ `503` means "unavailable", not "empty"

The API never fabricates data it does not have. If a projection is missing, still catching up, or
flagged as degraded, the affected read returns **`503`** rather than a plausible-looking zero.

Treat `503` as a freshness state, not a failure: show "temporarily unavailable" and retry. Rendering
zeros or an empty chart is wrong in the way that matters — it looks like an answer.

Some aggregate endpoints return partial results instead, and name the vaults they had to omit.
Check for those fields rather than assuming a complete set.

## Pagination

List endpoints use **opaque keyset cursors**:

```
GET /v2/referrer/{addr}/payouts?limit=50
→ { "data": { "payouts": [...], "nextCursor": "..." } }

GET /v2/referrer/{addr}/payouts?limit=50&cursor=<nextCursor>
```

* Pass `nextCursor` back verbatim. Never construct, decode, or mutate one.
* `nextCursor: null` means you have reached the end.
* There is no offset or page-number pagination. Cursors are stable under concurrent writes; offsets
  would not be.
* `limit` accepts 1–100.

## Dates and history

* Date filters (`startDate`, `endDate`, `from`, `to`) are **inclusive** and always UTC.
* Daily series contain **completed UTC days only**. Today never appears. Each response carries a
  watermark (`throughDate`) telling you the newest day covered — surface it, or users will report
  missing earnings that simply have not closed yet.
* Some historical rows predate our current data pipeline and are explicitly flagged as legacy or
  reconstructed. Do not present them as exact.

## Identifiers

Vaults are addressed by their **base58 on-chain address**. There is no numeric vault ID, and no
per-vault share-token mint — a position is a share balance tracked by the vault program, not a
transferable token.

If you are looking for a "vault token address", you want the vault address. If you are looking for
the deposit asset's mint, that is a separate field on the vault record.

## Previews are estimates

`simulate-deposit` and `simulate-withdraw` compute outcomes from current projected state without a
Solana RPC call. They are useful, and they are not promises:

* Deposit shares are estimated at the current share price. The program mints them during a later
  netting cycle, so a price move before netting changes the final result.
* Withdrawal amounts are recomputed at settlement, after cooldown.
* Previews take no user address, so they cannot check balances, allowlists, existing pending
  requests, or any user-specific fee or timing overrides.

A rejection on policy grounds — below minimum, over capacity, vault paused — returns `200` with a
structured `accepted: false` verdict. Malformed input returns `400`. Always validate the real
transaction against live state before asking a user to sign.

## Processing estimates

Fields describing when a request will process are **schedule-derived estimates, not commitments**.
They can be `null` when timing inputs are incomplete or a request has already reached a terminal
state. Do not build countdowns that imply certainty.

The underlying lock-up, cooldown, and redemption-window rules are documented in
[Fees + Redemption Period](../additional-info/fees-+-redemption-period.md).
