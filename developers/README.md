---
description: >-
  Programmatic access to Neutral Trade vault data, user positions, and builder-code
  earnings.
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

Neutral Trade exposes vault configuration, live performance, historical time series, user positions,
and builder-code earnings through a versioned REST API, a TypeScript SDK, and an on-chain program
IDL.

|                    |                                                                     |
| ------------------ | ------------------------------------------------------------------- |
| **Base URL**       | `https://api.neutral.trade`                                         |
| **Protocol**       | HTTPS, JSON                                                         |
| **Interactive spec** | [`https://api.neutral.trade/docs`](https://api.neutral.trade/docs) |
| **Machine-readable spec** | `https://api.neutral.trade/openapi.json`                     |
| **Where to call it from** | Backend / server-side. Never embed an API key in a browser or mobile client. |

## These docs versus the interactive spec

The interactive spec is the authoritative reference for **exact request parameters, response fields,
and status codes**. It is generated from the running service, so it is never out of date.

These pages exist for what a spec cannot tell you: which credential unlocks what, what the data
actually means, which guarantees hold, and which details will cost you a bug if you miss them. Read
these first, then use the spec while you build.

## Where to start

| You want to… | Start here |
| --- | --- |
| Understand what you can access and how to authenticate | [Access & authentication](access-and-authentication.md) |
| Avoid the mistakes that cost real money | [API conventions](api-conventions.md) |
| Pull vault performance, TVL, or user positions | [Vault & user data](vault-and-user-data.md) |
| Read your builder-code earnings | [Builder-code data](builder-code-data.md) |
| Move an existing integration off the old API | [Migrating from the legacy API](migrating-from-the-legacy-api.md) |
| Earn a fee share on deposits you refer | [How builder codes work](../for-distribution-partners/how-builder-codes-work.md) |
| Understand the commercial arrangement | [Distributors](../for-distribution-partners/distributors.md) |
| Understand how the vaults themselves work | [How They Work](../neutral-strategy-vaults/how-they-work.md) |

## SDK

The TypeScript SDK wraps the on-chain program and provides transaction builders the REST API
deliberately does not — including the single-transaction attributed deposit that distribution
partners need.

{% embed url="https://sdk.neutral.trade/" %}

## The API does not build transactions

The REST API is read-only by design and holds no Solana RPC connection. It can tell you what a
deposit or withdrawal **would** produce (`simulate-deposit`, `simulate-withdraw`), but it cannot
construct a transaction for a user to sign.

Use the SDK for anything that writes to the chain.

## IDL

The Anchor IDL describes the on-chain program that runs Neutral Trade vaults. Use it to decode
accounts and instructions, or to build transactions directly against the program.

* `ntbundle.json` — Anchor IDL (JSON)
* `ntbundle.ts` — typed IDL (TypeScript)

{% file src="../.gitbook/assets/ntbundle.json" %}

{% file src="../.gitbook/assets/ntbundle (1).ts" %}

## Support

Questions, key requests, and integration help: [@NeutralTradeWill on Telegram](https://t.me/NeutralTradeWill).
