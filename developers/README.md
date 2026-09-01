---
description: >-
  Programmatic access to vault data, unsigned transactions, user positions, and
  builder-code reporting.
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

# Developers

Neutral Trade provides a v2 REST API, a TypeScript SDK, and a Solana program IDL.

**REST base URL:** `https://api.neutral.trade`

**Interactive OpenAPI:** [api.neutral.trade/docs](https://api.neutral.trade/docs)

**Machine-readable OpenAPI:** `https://api.neutral.trade/openapi.json`

The running OpenAPI document is authoritative for exact parameters, response fields, and status
codes. These pages explain credential boundaries, financial meaning, and integration invariants.

## Start with the relevant guide

* [Access & authentication](access-and-authentication.md) explains public routes, partner keys, and
  wallet sessions.
* [API conventions](api-conventions.md) covers integer amounts, freshness, pagination, and
  transaction-builder responses.
* [Vault & user data](vault-and-user-data.md) explains configuration, performance, balances, and
  activity.
* [Builder-code data](builder-code-data.md) explains tiers, attributed users, earnings, history, and
  payouts.
* [Migrating from the legacy API](migrating-from-the-legacy-api.md) maps numeric v1 vault IDs and
  instruction builders to v2.
* [Integration guide](../for-distribution-partners/integration-guide.md) implements a strict
  attributed first deposit.

## Transactions

The REST API builds unsigned deposit and withdrawal transactions:

* `POST /v2/vault/{vaultAddress}/tx/deposit`
* `POST /v2/vault/{vaultAddress}/tx/withdraw`

Both are public, CORS-enabled, and metered by IP. The response provides an unsigned
`transactionBase64` and equivalent `instructions[]`. The server never signs or submits.

Use the TypeScript SDK when you need direct RPC state checks, program instruction composition,
registration plans, or builder claim helpers.

{% embed url="https://sdk.neutral.trade/" %}

## IDL

The current Anchor IDL includes the live builder tier configuration and referred-net-deposit state.
Use it to decode accounts and events or construct program interactions directly.

* `ntbundle.json` is the JSON IDL.
* `ntbundle.ts` is the typed TypeScript IDL.

{% file src="../.gitbook/assets/ntbundle.json" %}

{% file src="../.gitbook/assets/ntbundle.ts" %}

## Support

For keys and integration help, contact
[@NeutralTradeWill on Telegram](https://t.me/NeutralTradeWill).
