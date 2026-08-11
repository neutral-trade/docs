---
description: >-
  Which credential unlocks which part of the API, and why some endpoints stay
  closed even with a valid key.
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

Two independent things decide what you can call:

1. **Which credential you present** — nothing, an API key, or a portal session.
2. **Whether your wallet is a registered builder on chain** — this gates the earnings endpoints, and
   a valid API key alone does not unlock them.

Most integrators only ever need an API key.

## The three credentials

### No credential

A small set of endpoints is public by design. They are safe to call from a browser and consume no
quota.

| Endpoint | Purpose |
| --- | --- |
| `GET /public/codes/{code}` | Resolve a human-readable builder code to its current referrer address |
| `GET /public/yields` | Vault TVL and gross APY for yield aggregators |

`/public/codes/{code}` is CORS-enabled deliberately: it is what a partner's browser calls so their
API key never has to leave their server.

### API key — the data surface

Everything under `/v2/*` requires an API key. This is what almost every integration uses.

```bash
curl -H "x-api-key: YOUR_KEY" https://api.neutral.trade/v2/vaults

# Or:
curl -H "Authorization: Bearer YOUR_KEY" https://api.neutral.trade/v2/vaults
```

Keys are environment-bound. A `sandbox` key reads devnet data; a `prod` key reads mainnet. They are
not interchangeable, and the prefix tells you which you are holding: `nt_sandbox_…` or `nt_prod_…`.

**Server-side only.** A key in a browser bundle or mobile binary is a leaked key.

### Portal session — managing your organization

A short-lived session, obtained by signing a challenge with your organization's owner wallet
(Sign-In With Solana), authorizes the endpoints that manage your own account: profile, builder
codes, API keys, and owner-wallet rotation.

An API key **cannot** issue keys or claim codes, and a session **cannot** read the data surface.
They are separate credentials with separate jobs.

Sessions are handled for you by the [Partner Portal](../for-distribution-partners/partner-portal.md).
You only need to implement the flow directly if you are automating account management.

## What each tier unlocks

| Capability | Public | API key | API key + registered builder | Portal session |
| --- | :---: | :---: | :---: | :---: |
| Resolve a builder code | ✅ | ✅ | ✅ | — |
| Aggregator yield feed | ✅ | ✅ | ✅ | — |
| Vault directory, config, metrics, history | — | ✅ | ✅ | — |
| Share price and daily snapshots | — | ✅ | ✅ | — |
| Deposit / withdrawal previews | — | ✅ | ✅ | — |
| User balances, portfolio, activity, pending requests | — | ✅ | ✅ | — |
| Platform statistics | — | ✅ | ✅ | — |
| **Builder-code earnings, cohort, payouts, daily history** | — | ❌ | ✅ | — |
| **Your on-chain referral terms** | — | ❌ | ✅ | — |
| Manage profile, codes, API keys, owner wallet | — | — | — | ✅ |

## Why a valid key can still be refused

The earnings endpoints are addressed by referrer wallet — `/v2/referrer/{address}/…`. Your key
authorizes exactly one wallet: the owner wallet of the organization the key belongs to.

That means:

* Reading **your own** referrer address works, provided your organization has an owner wallet.
* Reading **anyone else's** referrer address returns `403`, always.
* An organization with no owner wallet returns `403` with an `OWNER_WALLET_REQUIRED` code — claim an
  owner wallet in the portal to resolve it.

If your organization is not a distribution partner, the earnings endpoints are simply not part of
your surface. Nothing else is affected.

## Getting a key

1. Sign in to the [Partner Portal](../for-distribution-partners/partner-portal.md) with your wallet.
2. Create your organization.
3. Issue a key — choose `sandbox` to build against devnet, `prod` when you go live.

**The plaintext key is shown exactly once.** Store it in your secret manager immediately. Only a hash
is retained, so a lost key must be rotated, not recovered.

### Rotation and revocation

* **Rotate** issues a replacement that preserves environment, scope, expiry, and quota. The old key
  keeps working for **60 seconds** so you can deploy without downtime, then stops.
* **Revoke** is immediate in our datastore and takes effect across all API instances within 60
  seconds.

Rotate on any suspicion of exposure — there is no downside beyond a deploy.

## Rate limits

Quotas are per key, in fixed windows. Rate-limited responses carry standard headers:

```
X-RateLimit-Limit
X-RateLimit-Remaining
X-RateLimit-Reset
```

Exceeding your quota returns `429` with `Retry-After`. Respect it — do not retry in a tight loop.
Public endpoints do not consume key quota.

Need a higher limit? Ask.

## Which vaults you can see

Your key sees **every vault registered to the current vault program**, whether or not it appears in
the public catalog on the website. Retired legacy vaults from the previous program are excluded.

Catalog metadata (`visible`, `private`) travels with each vault as a hint for how to present it in
your own UI. It does not restrict what the API returns, so apply your own filtering if you are
building a public catalog.
