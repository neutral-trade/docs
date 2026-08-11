---
description: >-
  What vault and user data the API exposes, what each dataset means, and how to
  answer the questions integrators usually have.
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

# Vault & user data

Available to any valid API key. Exact fields and parameters live in the
[interactive spec](https://api.neutral.trade/docs) — this page covers what the data means and how to
combine it.

## Vault data

| Group | What it gives you |
| --- | --- |
| **Directory & config** | Every registered vault: name, asset and decimals, fee schedule, capacity, minimums, lock and redemption policy, processing cadence |
| **Current metrics** | APR / APY, Sharpe, max drawdown, ROI, current TVL — gross and net of fees |
| **Metrics history** | The same risk and return measures as a dated daily series |
| **Share price** | Current lossless price per share, plus a series of ticks at event resolution |
| **Daily snapshots** | One row per vault per day: closing TVL, share price, shares outstanding, plus flow and fee aggregates |
| **Previews** | What a given deposit or withdrawal would produce, without building a transaction |
| **Platform statistics** | Cross-vault TVL, distinct active users, cumulative capital raised |

### Deriving yield yourself

There is no single stored "APY" constant. Yield comes from the change in **price per share** between
two dates, taken from the daily snapshot series. Current and blended figures are precomputed on the
metrics endpoint if you would rather not do it yourself.

The methodology behind our published figures is documented in
[APY and APR Calculations](../additional-info/apy-and-apr-calculations.md).

Metrics history does not retroactively apply today's fee schedule to past points. A fee change shows
up from the date it took effect, which is the honest representation but means a naive
recomputation from raw share prices will not match our published net figures exactly.

### Processing cadence

Vaults process deposits and withdrawals on a schedule rather than continuously. Each vault record
carries its cadence and processing time. This is what determines when a user's request actually
settles — surface it, or users will assume their deposit is stuck.

The lock-up, cooldown, and redemption-window rules behind those schedules are explained in
[Fees + Redemption Period](../additional-info/fees-+-redemption-period.md).

## User data

Addressed by wallet, either within one vault or across all of them.

| Group | What it gives you |
| --- | --- |
| **Balance** | A user's position in one vault: shares, current value, unpaid fee estimate |
| **Portfolio** | The same across every vault the user holds, with token-native and USD totals |
| **Activity** | Paginated deposit, withdrawal, and switch history |
| **Pending requests** | In-flight deposits and withdrawals with a processing estimate |
| **Interest earned** | Yield attributed to the user over a window |
| **Position history** | The user's position value as a dated series |

### Points worth knowing

* **Unpaid fee estimates use the vault-level fee schedule.** A user with an individual fee override
  will see a different figure on chain. Treat the estimate as indicative.
* **Portfolio omits vaults with degraded data** rather than reporting a wrong number, and lists them
  separately. Check that list before showing a total.
* **Aggregate freshness is the oldest contributing position**, not the newest. A portfolio's `asOf`
  is deliberately conservative.

## Common tasks

**"Show a user their yield since they deposited."**
Combine position history with activity to find the entry point, or read interest earned over the
window directly.

**"List vaults for a catalog page."**
Read the directory. Filter on the catalog metadata yourself — the API returns every registered vault,
including ones not shown on our own site.

**"Show a live APR on our marketing page."**
Use current metrics, and cache it. The underlying value updates on a daily cadence; polling faster
gains nothing and burns quota.

**"Tell a user when their withdrawal arrives."**
Read pending requests for the estimate, and show the vault's redemption schedule alongside it. The
estimate can be `null` — have a fallback message.

**"Reconcile our books monthly."**
Use daily snapshots and the daily flow aggregates, bounded by the response watermark. Do not
reconcile against live current-state reads; they move.

## What is not exposed

* **Strategy-internal venue allocations** — where a vault's capital sits across exchanges and
  protocols. This stays on our private stack.
* **Transaction building** — the API holds no RPC connection. Use the SDK.
