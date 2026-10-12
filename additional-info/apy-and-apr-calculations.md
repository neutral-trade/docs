---
description: >-
  How Neutral Trade calculates APR and APY from a vault's price per share, the
  time windows the app uses, target figures, and gross versus net.
---

# APY and APR Calculations

Every measured yield figure in the Neutral Trade app comes from one number: the vault's **price per share (PPS)**. This page explains how PPS becomes an APR and an APY, and how to read the figure you see on a vault.

## APR

APR compares the current price per share with the price per share at the start of a time window, then annualizes the result. It is a simple annualization with no compounding.

```
return = (PPS_end - PPS_start) / PPS_start
APR    = return * (365 / days in window)
```

## APY

APY converts APR with daily compounding:

```
APY = (1 + APR / 365) ^ 365 - 1
```

## Time Windows

The app calculates yield over three windows: **30 days, 90 days, and All**. On a strategy page you can switch between the windows.

* The headline figure on a vault is the highest of the available windows. The tooltip on the APY shows which window is in use.
* A short window reacts quickly to recent performance. A long window is steadier and includes more market conditions.
* **All** is the full track record. On a vault with a Pre-Neutral track record, the All basis includes that record. The live basis does not.

## Target Figures on New Vaults

Until a vault has 60 days of live history, the app can show a **target** APR or APY. A target is marked with a dashed underline. It is an objective that comes from the strategy's earlier track record or backtest. It is not a measured return on Neutral Trade, and it is not a commitment.

When the vault has enough live history, the target is replaced by the measured windows.

## Gross and Net

* **Gross** figures are before fees.
* **Net** figures are after the vault's management fee and performance fee.

The tooltip on the APY shows both. Your own result also depends on your entry date, your high-water mark, and any VIP discount. See [Fees + Redemption Period](fees-+-redemption-period.md).

## Pre-Launch Track Record

Some vaults show a track record from before the strategy was listed on Neutral Trade. The app marks this period as **Pre-Neutral** and lets you switch between the full track record and the period on Neutral Trade.

## What These Numbers Are Not

A measured APR or APY describes past performance over a stated window. A target describes an objective. Neither is a forecast or a guarantee. A vault with a positive APY can still have losing weeks and months. Check the Sharpe ratio, the maximum drawdown, and the monthly returns on the vault page, and read the [Risk Overview](../for-capital-allocators/risk-overview/).

## Common Questions

**Is the APY guaranteed?**

No. A measured APY is a historical figure, and a target APY is an objective.

**What does a dashed underline on an APY mean?**

The figure is a target, shown because the vault does not yet have 60 days of live history.

**Why does the APY change when I switch the window?**

Each window measures a different period. A strategy that had a strong month shows a higher 30-day figure than its 90-day or All figure.

**Is the headline APY before or after fees?**

The tooltip on the APY shows the gross and the net figure, so you can read both.
