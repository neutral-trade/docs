---
description: >-
  Current REST API, TypeScript SDK, and Solana program IDL entry points for
  vault and builder integrations.
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

# API, SDK & IDL

Neutral Trade exposes current vault data, unsigned transaction builders, user positions, and
builder reporting through a versioned REST API. The TypeScript SDK provides direct Solana program
clients and composable instruction builders. The IDL is available for integrations that need to
decode or construct program interactions themselves.

## REST API

**Base URL:** `https://api.neutral.trade`

**Interactive OpenAPI:** [api.neutral.trade/docs](https://api.neutral.trade/docs)

**Machine-readable OpenAPI:** `https://api.neutral.trade/openapi.json`

Current API paths use base58 vault account addresses. Numeric legacy `vaultId` values are not valid
v2 identifiers.

Public browser-safe routes include:

* `GET /public/codes/{code}` to resolve a human-readable builder code.
* `GET /public/yields` for the aggregator yield feed.
* `POST /v2/vault/{vaultAddress}/tx/deposit` to build an unsigned deposit transaction.
* `POST /v2/vault/{vaultAddress}/tx/withdraw` to build an unsigned withdrawal request.

The two transaction builders use open CORS and per-IP metering. They never hold a private key,
sign, submit, or custody funds. An optional partner key can select the partner's own quota and add
operational identity, but it must not be placed in browser code.

A valid partner API key unlocks authenticated vault, user, platform, and referrer reporting. See
[Developers](../developers/) for conventions and endpoint groups.

The vault directory exposes each vault's live referral configuration, including the enabled flag
and ordered tier schedule. Tier thresholds are raw values in the vault asset's minor units.

## Builder integration

For a referred first deposit, call the public deposit builder with a `referrer` address or
human-readable `code` and set `requireAttribution: true`. An accepted response contains both:

* `transactionBase64`, an unsigned Solana v0 transaction with a fresh blockhash.
* `instructions[]`, the same instruction set in the legacy wire shape for custom composition.

The strict flag prevents a soft attribution failure from becoming a successful unattributed first
deposit. See the [integration guide](integration-guide.md).

## TypeScript SDK

The current `@neutral-trade/sdk` uses `@solana/kit` v6 and requires Node.js 20 or newer.

{% embed url="https://sdk.neutral.trade/" %}

Builder-focused helpers include:

* `buildAttributedDepositTx` for atomic account initialization, builder binding, deposit request,
  and points memo instructions.
* `buildBuilderRegistrationTx` for per-vault registration and any required builder deposit.
* `buildReferrerWithdrawRequestTx` for builder claim requests.
* `calculateReferrerTierScheduleProgress` for current and next-tier display.
* `resolveBundleReferralRates` and `resolveEffectiveReferralRates` for program-equivalent live
  rate resolution.

The SDK returns instructions or transaction plans. Your application remains responsible for
constructing the final transaction where required, presenting it to the signer, and submitting it.

## IDL

The Anchor IDL describes the Neutral Strategy Vault program. The current artifacts include the
referral tier schedule, referred net deposits, effective fee-rate events, builder registration, and
claim instructions introduced for the launched rebate mechanism.

* `ntbundle.json` is the JSON IDL.
* `ntbundle.ts` is the typed TypeScript IDL.

{% file src="../.gitbook/assets/ntbundle.json" %}

{% file src="../.gitbook/assets/ntbundle.ts" %}

Use the IDL to decode accounts and events or build directly against the program. Prefer the SDK
helpers for ordinary integrations because they enforce account ordering and eligibility checks.

Existing v1 clients should follow
[Migrating from the legacy API](../developers/migrating-from-the-legacy-api.md).
