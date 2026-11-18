---
description: >-
  Public routes, partner API keys, wallet sessions, and the access boundary for
  builder reporting.
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

# Access & authentication

Neutral Trade uses three access contexts: public browser routes, partner API keys, and short-lived
wallet sessions.

## Public routes

No credential is required for:

* `GET /public/codes/{code}`
* `GET /public/yields`
* `POST /v2/vault/{vaultAddress}/tx/deposit`
* `POST /v2/vault/{vaultAddress}/tx/withdraw`

The code resolver and transaction builders use browser CORS. Transaction builds are metered by IP.
They return unsigned data only; the connected user remains the sole transaction signer.

Do not add a partner key to frontend code. A trusted server may optionally authenticate a
transaction build to use its key quota and add partner identity to operational logs.

## Partner API keys

Authenticated data reads accept either header form:

```bash
curl -H "x-api-key: YOUR_KEY" https://api.neutral.trade/v2/vaults

curl -H "Authorization: Bearer YOUR_KEY" https://api.neutral.trade/v2/vaults
```

Keys belong in a backend or secret-managed job. They unlock the permitted v2 vault, user, platform,
and builder reporting surfaces.

{% hint style="info" %}
Referrer reporting is not owner-wallet gated. Any valid partner API key can request
`/v2/referrer/{address}/summary`, `payouts`, `history`, `users`, or `flows` for any valid
referrer address. These projections derive from public Solana activity.
{% endhint %}

`GET /v2/partner/agreements` is different. It resolves current terms for the owner referrer
associated with the authenticated partner, including the live tier or any configured override.

Environment-bound keys are not interchangeable. Where sandbox and production keys are issued,
their prefixes identify the environment. The current builder dashboard issues a production key for
the launched mainnet flow.

## Wallet sessions

The builder dashboard uses Sign-In With Solana message signatures to create a short-lived,
HTTP-only session for organization and credential management.

A new builder wallet is provisioned into the self-service partner flow automatically. The launched
dashboard does not require a separate legal-entity form or manual KYB approval before builder
registration and key issuance.

The session manages the wallet's own control-plane resources, such as human-readable codes, API
keys, and organization ownership. It is separate from an API key and should not be used as a data
read credential.

## Create and store a key

Open the [builder dashboard](../for-distribution-partners/partner-portal.md), go to Integration, and
sign the requested wallet message.

The plaintext key is displayed once. Store it immediately in a secret manager. Neutral Trade keeps
only a hash, so the original value cannot be recovered.

The dashboard's Generate key flow issues a replacement and revokes earlier active keys. The direct
partner API also supports:

* **Issue** to create an additional scoped key.
* **Rotate** to issue a replacement while the old key remains valid for 60 seconds.
* **Revoke** to disable a key, with distributed auth caches observing the change within 60 seconds.

Use the interactive OpenAPI document for the current control-plane request schemas.

## Rate limits

Authenticated quotas are per key and use fixed windows. Rate-limited responses include
`X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset`, and `Retry-After` where
applicable.

Respect HTTP 429 and wait for the indicated reset. Public transaction builders use their own per-IP
meter rather than consuming a hidden browser key.

## Vault visibility

A partner key can see every vault registered to the current Neutral Strategy Vault program,
including records not shown in the public catalog. Apply the returned `visible`, `private`,
`enabled`, and `deprecated` metadata when building a public-facing list.

