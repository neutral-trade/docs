# Options Market Making

## Overview

Options MM is a market-neutral strategy vault managed by Xanthas, an institutional crypto options market maker. The strategy targets volatility and relative-value opportunities through continuous options market making and multi-leg options trading, supported by systematic risk management and a low-latency execution stack. Returns are driven by volatility and relative-value capture rather than the direction of the underlying.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>DEPOSIT</td><td><a href="https://www.neutral.trade/strategies/options-mm-z">https://www.neutral.trade/strategies/options-mm-z</a></td></tr></tbody></table>

_Live on Neutral Trade: 14 July 2026_

_Past performance is not indicative of future results._

## How it works

Xanthas runs an automated options market-making system that generates systematic quoting signals across the Bitcoin volatility surface, with a particular edge in multi-leg structures including calendars, butterflies, verticals, and risk reversals, sourced through institutional RFQ networks alongside central-limit-order-book (CLOB) quoting. Directional exposure from the options book is hedged via perpetual futures to maintain a delta-neutral posture.

The core engine is built around an arbitrage-free eSSVI volatility surface and a Bates-Kou jump-diffusion model calibrated to Bitcoin's asymmetric return profile.

### **Venues**

**Centralized:** OKX

### Yield Sources

* **Variance risk premium:** captured through short-dated volatility selling.
* **Relative-value capture:** edge from trading multi-leg options structures: calendars, butterflies, verticals, and risk reversals, sourced via institutional RFQ networks alongside CLOB quoting.

## Risk Factors

**Volatility and jump risk:** The strategy is delta-neutral to BTC price direction but retains exposure to changes in implied volatility (vega) and to large sudden price moves (gamma and jumps). A volatility spike or a sharp BTC move can produce mark-to-market losses. Mitigations: a Bates-Kou jump-diffusion model calibrated to Bitcoin's asymmetric return profile prices the likelihood of sharp moves, and the risk framework includes dedicated vega management.

**Adverse selection risk:** As a market maker, the strategy can be filled on the wrong side of an informed move, eroding spread income. Mitigations: a jump-diffusion pricing model reduces pricing error on out-of-the-money options, directly reducing adverse selection on wing trades.

**Hedging and funding risk:** Directional exposure is hedged with perpetual futures. The hedge incurs funding costs that can be positive or negative, and hedge adjustments incur transaction costs. Perpetual future positions are also subject to exchange margin requirements and Auto-Deleveraging (ADL). Mitigations: charm-aware hedging reduces the frequency of hedge adjustments (reduced costs), and the risk framework includes funding rate hedging.

**Counterparty and exchange risk:** Trading on a centralised venue creates exposure to venue-level failure, insolvency, or operational disruption. Mitigations: off-exchange custody and settlement via Copper, so assets remain with the custodian rather than on the exchange balance sheet.

**Operational and execution risk:** The strategy runs as automated software executing via API on the exchange account, and depends on continuous availability of connectivity, exchange APIs, and infrastructure. Disruption at any layer can prevent timely quoting or hedging. Mitigations: a defence-in-depth control stack including exchange-native market-maker-protection groups and cancel-on-disconnect at the lowest latency layer, and independent software circuit breakers above it.

