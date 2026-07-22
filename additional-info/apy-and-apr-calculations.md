# APY and APR Calculations

APR is calculated using the current PPS (Price Per Share) compared to the PPS from a previous period. 90 days is common, though it can vary depending on the age of the vault and various other factors.

This specific information, along with gross and net APY, is visible when you hover over the APY icon on any given vaults page in our app.

While APR is based on historical performance and not guaranteed, it provides a clear insight into what depositors earned during that timeframe. APR is gross, before fees.

**`APR = returns * (365 / daysElapsed)`**\
&#xNAN;**`daysElapsed = past 90 days`**\
\&#xNAN;**`Returns = (end value - start value) / start value`**

For APY figures we use the daily compounding formula:

```
APY=(1+APR/365)*365−1
```
