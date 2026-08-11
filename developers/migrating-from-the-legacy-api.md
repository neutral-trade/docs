---
description: >-
  Moving an integration from www.neutral.trade/api/v1 to api.neutral.trade —
  what maps across, what changes shape, and what moves to the SDK.
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

# Migrating from the legacy API

If you integrated against `https://www.neutral.trade/api/v1`, this page is your migration path to
`https://api.neutral.trade`.

**Your existing API key continues to work.** The new API accepts the same headers, so authentication
needs no change.

## The three things that change

1. **Base URL** — `https://www.neutral.trade/api/v1` → `https://api.neutral.trade/v2`
2. **Vault identifier** — numeric `vaultId` → base58 on-chain vault address
3. **Response shape** — bare objects → a `{ success, data, asOf }` envelope, with token amounts as
   raw integer strings rather than JSON numbers

The identifier change touches every call. Map your stored vault IDs to addresses once, from the new
vault directory, rather than translating per request.

## Endpoint mapping

| Legacy endpoint | Replacement |
| --- | --- |
| `GET /vaults` | `GET /v2/vaults` |
| `GET /vault/{vaultId}/config` | `GET /v2/vault/{address}` |
| `GET /vault/{vaultId}/metrics` | `GET /v2/vault/{address}/metrics` |
| `GET /vault/{vaultId}/snapshots` | `GET /v2/vault/{address}/snapshots` |
| `GET /vault/{vaultId}/deposit-instructions` | **No REST equivalent — use the SDK** |
| `GET /vault/{vaultId}/withdraw-instructions` | **No REST equivalent — use the SDK** |

{% hint style="warning" %}
**The two instruction-builder endpoints have no replacement in the new API.**

The new API is read-only by design and holds no Solana RPC connection, so it cannot construct
transactions. If you use `deposit-instructions` or `withdraw-instructions`, that part of your
integration moves to the [TypeScript SDK](https://sdk.neutral.trade/) — it is not a URL swap.

Plan for this. It is the only part of the migration that requires real work.
{% endhint %}

## What you gain

The new API covers considerably more than the legacy one:

* **User data** — balances, portfolios, activity history, pending requests, interest earned
* **Position history** — dated series per user, per vault or across all
* **Metrics history** — APR, APY, Sharpe, and drawdown as a time series rather than a snapshot
* **Share-price ticks** at event resolution, not just daily closes
* **Deposit and withdrawal previews** without building a transaction
* **Platform statistics** — cross-vault TVL, active users, capital raised
* **Builder-code earnings**, for distribution partners
* **Self-serve key management** — issue, rotate, and revoke your own keys in the portal

## Response differences to handle

### The envelope

```jsonc
// Legacy
{ "vaultId": 48, "name": "…", "currentTVLUSD": 1234567.89 }

// New
{
  "success": true,
  "data": { "…": "…" },
  "asOf": { "slot": 300000000, "blockTime": 1800000000 }
}
```

`asOf` tells you which chain position the data reflects. Use it for freshness display.

### Numbers

Legacy responses used JSON numbers. The new API returns token amounts, share counts, and share
prices as **raw integer strings in the asset's smallest unit**, with an exact decimal rendering
alongside for display.

Parse with `BigInt`. See [API conventions](api-conventions.md#token-amounts-are-strings-and-must-stay-that-way)
— this is where migrations most often introduce a silent precision bug.

### USD values can be null

`null` means no current price was available, not zero. Render it as unavailable.

### `503` is meaningful

The new API returns `503` rather than inventing data when a projection is missing or degraded. Your
error handling should treat it as "retry", not as an outage, and must not fall back to rendering
zeros.

## Suggested sequence

1. Pull `GET /v2/vaults` and build your `vaultId` → address map.
2. Point read paths at the new base URL, one endpoint at a time.
3. Convert number handling to `BigInt` **before** going live — this is the step that fails quietly.
4. Migrate any instruction-building to the SDK.
5. Rotate your API key in the portal once you are cut over, since the legacy key predates self-serve
   key management.

## Legacy API status

The legacy API remains available for now. We will give notice before it is retired, and we would
rather hear from you than surprise you — tell us what you still depend on:
[@NeutralTradeWill on Telegram](https://t.me/NeutralTradeWill).
