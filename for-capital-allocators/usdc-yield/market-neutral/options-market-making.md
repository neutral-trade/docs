---
description: >-
  A market-neutral systematic Bitcoin options strategy on OKX that earns the
  variance risk premium, with off-exchange custody through Copper. USDC deposits
  on Solana.
---

# Options Market Making

## Overview

Options Market Making is a market-neutral strategy vault curated by Xanthas. It runs systematic Bitcoin options software that sells short-dated BTC option structures when implied volatility is rich compared with a proprietary three-day realised-volatility forecast. Directional exposure is hedged with perpetual swaps, so returns come from the persistent variance risk premium in crypto options markets, not from the direction of the market.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>DEPOSIT</td><td><a href="https://www.neutral.trade/strategies/options-mm-z">https://www.neutral.trade/strategies/options-mm-z</a></td></tr></tbody></table>

_Live on Neutral Trade: 14 July 2026_

_Past performance is not indicative of future results._

## How it works

1. **Forecast.** The software forecasts Bitcoin's realised volatility over the next three days with a proprietary model.
2. **Sell rich volatility.** When implied volatility in the BTC options market is rich compared with that forecast, the software sells short-dated BTC option structures. Automated signals generate the trades within pre-configured risk parameters.
3. **Hedge direction.** Directional exposure from the options book is hedged with perpetual swaps to keep the book delta-neutral.
4. **Execute automatically.** Custom order handlers run the strategy on the trading account through trade-only API credentials. Xanthas never holds the capital.

### **Venues**

**Centralized:** OKX, with off-exchange custody and settlement through Copper.

### Yield Sources

* **Variance risk premium:** implied volatility in crypto options tends to be priced above the volatility that is later realised. The strategy captures this gap by selling short-dated volatility when it is rich.

## Risk Factors

**Volatility and jump risk:** The strategy is delta-neutral to BTC price direction but keeps exposure to changes in implied volatility (vega) and to large sudden price moves (gamma and jumps). Short option positions lose money when realised volatility is higher than the volatility that was sold, so a volatility spike or a sharp BTC move can produce mark-to-market losses. Mitigations: trades are sized and limited by pre-configured risk parameters, and positions are short-dated.

**Model risk:** The strategy depends on its three-day realised-volatility forecast. If the forecast is wrong, the strategy can sell volatility that is not rich. Mitigations: pre-configured risk parameters limit the size of each position.

**Hedging and funding risk:** Directional exposure is hedged with perpetual swaps. The hedge has funding costs that can be positive or negative, and hedge adjustments have transaction costs. Perpetual positions are also subject to exchange margin requirements and Auto-Deleveraging (ADL).

**Counterparty and exchange risk:** Trading on a centralised venue creates exposure to venue-level failure, insolvency, or operational disruption. Mitigations: off-exchange custody and settlement through Copper, so assets remain with the custodian rather than on the exchange balance sheet.

**Operational and execution risk:** The strategy runs as automated software through the exchange API and depends on connectivity, exchange APIs and infrastructure. Disruption at any layer can prevent timely trading or hedging. Mitigations: the API credentials are trade-only, so the curator can trade the account but cannot withdraw from it.

## Why Xanthas?

Xanthas is an eight-person team with experience from Societe Generale, Tower Research Capital, B2C2, Goldman Sachs and Graham Capital. Quant, engineering and trade operations are in house, with no offshore contractors.

{% hint style="info" %}
Xanthas is an alias. We've excluded the curator's full name to mitigate alpha leaking. Neutral Trade has completed thorough due diligence on the team and its strategy.
{% endhint %}
