---
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
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

# API & SDK & IDL

Neutral Trade exposes vault configuration, live performance, and full historical time-series through a versioned REST API, a TypeScript SDK, and an on-chain program IDL. This page is the integration reference for distribution partners, allocators, and anyone pulling Neutral Trade data programmatically.

{% hint style="info" %}
**Key concept — vaults are identified by a numeric `vaultId`.**

Neutral Trade vaults do **not** have per-vault share-token mint addresses. There is no SPL token mint that represents a vault or a depositor's position, and no "vault token contract" to look up. Every vault is addressed by its integer `vaultId`, and all configuration, performance, and historical data is retrieved from the REST API using that ID. If you are looking for a "vault token address," use the `vaultId` instead.
{% endhint %}

### REST API

**Interactive reference (OpenAPI / Swagger):**

{% embed url="https://www.neutral.trade/api/v1/docs" %}

|                           |                                                                                                                                                                                                                         |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Base URL**              | `https://www.neutral.trade/api/v1`                                                                                                                                                                                      |
| **Protocol**              | HTTPS, JSON request/response                                                                                                                                                                                            |
| **Authentication**        | API key, server-to-server. Pass your key in the request header (see the **Authorize** dialog in the interactive docs for the exact header name). Keys are issued by Neutral Trade — contact the team to request access. |
| **Rate limit**            | 1,000 requests per 10 minutes, per key                                                                                                                                                                                  |
| **Where to call it from** | Backend / server-side only. Do not embed API keys in browser or mobile clients.                                                                                                                                         |

#### Endpoints

| Method | Path                         | Returns           | Description                                                                                                           |
| ------ | ---------------------------- | ----------------- | --------------------------------------------------------------------------------------------------------------------- |
| `GET`  | `/vaults`                    | `VaultConfig[]`   | List every vault with its static configuration.                                                                       |
| `GET`  | `/vault/{vaultId}/config`    | `VaultConfig`     | Static configuration for a single vault.                                                                              |
| `GET`  | `/vault/{vaultId}/metrics`   | `VaultMetrics`    | Current performance metrics — APR, TVL, ROI, Sharpe, drawdown, allocations.                                           |
| `GET`  | `/vault/{vaultId}/snapshots` | `DailySnapshot[]` | Full daily historical time-series — TVL, price-per-share, shares. The source for all historical APY/APR and PnL data. |

Deposit and withdrawal **instruction-builder** endpoints (which return unsigned Solana transactions for a depositor to sign) are also available — see the interactive reference for their exact request bodies and response shapes.

{% hint style="warning" %}
The interactive OpenAPI reference at `/api/v1/docs` is always the authoritative source for exact request parameters, response types, the authentication header, and any endpoints added after this page was written.
{% endhint %}

#### Active vault IDs

As of June 2026 the live vaults are:

```
48, 60, 65, 71, 72, 74, 75, 78
```

When pulling "all vaults," filter to this active set unless you specifically need deprecated or historical vaults. Each vault record also carries `enabled` and `deprecated` flags so you can filter programmatically.

#### How historical APY / APR is derived

There is no single stored "APY" constant. Yield is **computed from the daily snapshot series**:

* `GET /vault/{vaultId}/snapshots` returns one record per day, each containing `pps` (price per share) and `tvl`.
* APR/APY over any window is derived from the change in `pps` between two dates.
* Pre-computed current and blended figures (`apr`, `aprAfterFees`, `yieldApr`, `roi30d`, `roiSince`) are returned directly by `GET /vault/{vaultId}/metrics`.

***

#### Schema: `VaultConfig`

Static, slowly-changing configuration for a vault.

| Field                  | Type             | Description                                                                                                                                   |
| ---------------------- | ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| `vaultId`              | number           | Unique numeric identifier. **This is how every vault is referenced across the API.**                                                          |
| `name`                 | string           | Display name of the vault / strategy.                                                                                                         |
| `subname`              | string           | Secondary label (e.g. curator or sub-strategy).                                                                                               |
| `type`                 | string           | Vault type / architecture.                                                                                                                    |
| `category`             | string           | Strategy category (e.g. market-neutral, directional).                                                                                         |
| `chain`                | string           | Settlement chain (Solana).                                                                                                                    |
| `vaultAddress`         | string           | The vault's on-chain account address. This is the vault account — **not** a share-token mint.                                                 |
| `depositToken`         | string           | Symbol of the accepted deposit asset (e.g. USDC).                                                                                             |
| `depositTokenAddress`  | string           | SPL mint address of the **deposit** token (e.g. the USDC mint). This is the only token mint involved — there is no separate share-token mint. |
| `depositTokenDecimals` | number           | Decimals of the deposit token.                                                                                                                |
| `tvlCap`               | number           | Maximum vault capacity, in deposit-token units.                                                                                               |
| `minDepositAmount`     | number           | Minimum deposit, in deposit-token units.                                                                                                      |
| `minWithdrawAmount`    | number           | Minimum withdrawal, in deposit-token units.                                                                                                   |
| `depositLock`          | number / boolean | Whether (and how long) deposits are locked.                                                                                                   |
| `redeemLock`           | number / boolean | Whether (and how long) redemptions are locked.                                                                                                |
| `processFrequency`     | string           | How often deposits/withdrawals are processed (the redemption-window cadence).                                                                 |
| `processTime`          | string           | When processing occurs.                                                                                                                       |
| `performanceFee`       | number           | Performance fee rate.                                                                                                                         |
| `managementFee`        | number           | Management fee rate.                                                                                                                          |
| `depositFee`           | number           | Deposit fee rate.                                                                                                                             |
| `withdrawalFee`        | number           | Withdrawal fee rate.                                                                                                                          |
| `enabled`              | boolean          | Whether the vault is live and accepting activity.                                                                                             |
| `private`              | boolean          | Whether the vault is private / unlisted.                                                                                                      |
| `deprecated`           | boolean          | Whether the vault is deprecated. Deprecated vaults are kept for historical access but are no longer active.                                   |
| `ntMultiplier`         | number           | NT Points multiplier for the vault.                                                                                                           |
| `bundleProgramId`      | string           | The on-chain Solana program ID that runs the vault (the NT "bundle" program). Shared across vaults of the same architecture.                  |

#### Schema: `VaultMetrics`

Current, frequently-updated performance metrics.

| Field                   | Type           | Description                                                   |
| ----------------------- | -------------- | ------------------------------------------------------------- |
| `vaultId`               | number         | Vault identifier.                                             |
| `name`                  | string         | Vault name.                                                   |
| `apr`                   | number         | Current annualized percentage rate (gross).                   |
| `aprDayApplied`         | number         | Number of days of data the APR calculation is based on.       |
| `aprAfterFees`          | number         | APR net of fees.                                              |
| `yieldApr`              | number         | Yield-only APR (gross).                                       |
| `yieldAprAfterFees`     | number         | Yield-only APR, net of fees.                                  |
| `sharpeRatio`           | number         | Sharpe ratio of the strategy.                                 |
| `currentTVLUSD`         | number         | Current total value locked, in USD.                           |
| `currentTVLInToken`     | number         | Current TVL, in deposit-token units.                          |
| `maxDrawdown`           | number         | Maximum historical drawdown.                                  |
| `roi`                   | number         | Return on investment since inception.                         |
| `roi30d`                | number         | Trailing 30-day ROI.                                          |
| `roiSince`              | string (date)  | Inception / start date that `roi` is measured from.           |
| `allocations`           | array / object | Current strategy allocations / venue breakdown.               |
| `dateFromSnapshot`      | string (date)  | Date of the snapshot these metrics were computed from.        |
| `isAprTargeted`         | boolean        | `true` if the displayed APR is a target rather than realized. |
| `isMaxDrawdownTargeted` | boolean        | `true` if max drawdown is a target rather than realized.      |
| `isSharpeRatioTargeted` | boolean        | `true` if the Sharpe ratio is a target rather than realized.  |

#### Schema: `DailySnapshot`

One record per vault per day — the historical time-series backing all charts and yield calculations.

| Field               | Type          | Description                                                                                                              |
| ------------------- | ------------- | ------------------------------------------------------------------------------------------------------------------------ |
| `date`              | string (date) | Calendar date of the snapshot.                                                                                           |
| `tvl`               | number        | Total value locked on that date.                                                                                         |
| `pps`               | number        | Price per share on that date. Yield / APR is derived from changes in `pps` over time.                                    |
| `pps_before_offset` | number        | Price per share before fee / offset adjustment.                                                                          |
| `shares`            | number        | Total shares outstanding on that date.                                                                                   |
| `isBacktest`        | boolean       | `true` if the row is backtested / simulated rather than live. Exclude backtest rows when reporting realized performance. |

{% hint style="info" %}
A depositor's position value = their share count × `pps`. Shares are tracked by the vault and exposed through the API by `vaultId` — there is no transferable share-token mint to query on-chain.
{% endhint %}

#### Example requests

```bash
# Replace the auth header with the scheme shown in /api/v1/docs (Authorize dialog)

# List active vaults
curl -H "x-api-key: YOUR_API_KEY" \
  https://www.neutral.trade/api/v1/vaults

# Current metrics for vault 48
curl -H "x-api-key: YOUR_API_KEY" \
  https://www.neutral.trade/api/v1/vault/48/metrics

# Full daily history for vault 48 (the historical-APY source)
curl -H "x-api-key: YOUR_API_KEY" \
  https://www.neutral.trade/api/v1/vault/48/snapshots
```

### SDK

**TypeScript SDK:**

{% embed url="https://sdk.neutral.trade/" %}

The SDK wraps the REST API and the on-chain program, exposing typed methods for reading vault data and building deposit / withdraw transactions. See the embedded SDK reference for installation and usage.

### IDL

The Interface Definition Language (IDL) files describe the on-chain Solana program (Anchor IDL) that powers Neutral Trade vaults — the "bundle" program referenced by `bundleProgramId` in `VaultConfig`. Use them to decode accounts and instructions, or to build transactions directly against the program.

* `ntbundle.json` — Anchor IDL (JSON)
* `ntbundle.ts` — typed IDL (TypeScript)

{% file src="../.gitbook/assets/ntbundle.json" %}

{% file src="../.gitbook/assets/ntbundle (1).ts" %}
