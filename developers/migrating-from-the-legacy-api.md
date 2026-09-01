---
description: >-
  Move from www.neutral.trade/api/v1 to api.neutral.trade/v2, including current
  REST replacements for deposit and withdrawal instruction builders.
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

The current REST API is served from `https://api.neutral.trade`. Existing integrations using
`https://www.neutral.trade/api/v1` should migrate to v2.

Existing API-key header forms remain supported, but every migrated client should verify its key
scope and current quota against the running OpenAPI document.

## Core changes

**Base URL:** move from `https://www.neutral.trade/api/v1` to
`https://api.neutral.trade/v2`.

**Vault identifier:** replace numeric `vaultId` values with the base58 vault account address
returned by `GET /v2/vaults`.

**Response shape:** read `{ success, data, asOf }` envelopes rather than bare objects.

**Amounts:** parse token and share amounts as raw integer strings with `BigInt`, not JSON numbers.

## Read endpoint mapping

Use these current replacements:

* `GET /vaults` becomes `GET /v2/vaults`.
* `GET /vault/{vaultId}/config` becomes `GET /v2/vault/{vaultAddress}`.
* `GET /vault/{vaultId}/metrics` becomes
  `GET /v2/vault/{vaultAddress}/metrics`.
* `GET /vault/{vaultId}/snapshots` becomes
  `GET /v2/vault/{vaultAddress}/snapshots`.

Build a durable numeric-ID-to-address map from the vault directory before changing individual
calls.

## Transaction builder mapping

v2 now has direct REST replacements for both legacy instruction builders:

* Deposit instructions become
  `POST /v2/vault/{vaultAddress}/tx/deposit`.
* Withdrawal instructions become
  `POST /v2/vault/{vaultAddress}/tx/withdraw`.

The new routes return the same transaction in two forms:

* `transactionBase64` for clients that want a complete unsigned Solana v0 transaction.
* `instructions[]` in the legacy wire shape for clients that still compose their own message.

The routes are public and CORS-enabled. Do not expose a partner API key in a browser. The server
builds and preflights but never signs or submits.

For a builder-attributed deposit, include either `code` or `referrer` and set
`requireAttribution: true`. This is a functional improvement over the legacy path because it can
atomically bind the user's first deposit to a registered builder.

Withdrawal accepts `amountRaw` or `withdrawAll: true`.

## Response handling changes

**Lossless integers:** use raw minor-unit strings and `BigInt`. Convert to a display decimal only
after applying asset decimals.

**Nullable USD:** null means pricing is unavailable, not zero.

**HTTP 503:** treat it as temporarily unavailable and retry. Do not render empty data.

**Policy validation:** a well-formed request can return HTTP 200 with
`validation.accepted: false` and no transaction.

**Expiry:** submit an unsigned transaction before `lastValidBlockHeight`, then rebuild after
expiry.

## Migration sequence

* Pull `GET /v2/vaults` and persist the address mapping.
* Move reads to the v2 envelope and base58 paths.
* Convert all canonical amount handling to `BigInt`.
* Replace legacy instruction routes with the v2 POST transaction builders.
* Add strict attribution checks to any builder referral flow.
* Test signing, submission, expiry, and policy rejection with a fresh wallet.
* Rotate the integration key after cutover if the existing key has had a long lifetime.

Use [API conventions](api-conventions.md) while migrating and confirm exact schemas at
[api.neutral.trade/docs](https://api.neutral.trade/docs).

