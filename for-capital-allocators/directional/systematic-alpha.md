# Systematic Alpha

## Overview

Systematic Alpha is a systematic strategy on US equities that combines two complementary signals, mean-reversion and trend-following, into a single system. Unlike the market-neutral vaults on this platform, this strategy is **directional**: it carries directional long exposure to US equities (long-only, no short selling).

Because the two signals operate in different market environments, at least one engine aims to be generating alpha in any market regime. The strategy is built for allocators operating on a quarterly-to-annual horizon, not those reacting to a few days of NAV movement, and its primary objective is minimizing drawdown, not maximizing return.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies/systematic-alpha">https://www.neutral.trade/strategies/systematic-alpha</a></td></tr></tbody></table>

_Live on Neutral Trade: July 6, 2026_

_Past performance does not guarantee future results._

## How it works

The strategy does not depend on a single market, a single signal, or a single trading pattern. A single source of alpha disappears when market structure shifts, so the strategy runs two complementary signals simultaneously.

### **Mean-reversion**

When price diverges from a reference level, the strategy scales in at pre-defined ratios proportional to the size of the divergence, and exits as price reverts toward the reference. It generates alpha in volatile, range-bound, and corrective regimes.

### **Trend-following**

When the market forms a trend, the strategy scales in and scales out, closing at target profit or on a regime change. It generates alpha when the market moves strongly in one direction.

### **Per-asset models**

Each asset differs in volatility, mean-reversion strength, and trend persistence. Rather than applying one model to all assets, the strategy runs separately-validated parameter sets per asset.

### **Position holding**

Positions are typically held 3 to 5 days and are not structurally locked in for long periods. The strategy is long-only and does not take short positions.

### **Adaptive capital deployment**

The strategy is not always fully exposed to the market. Capital exposure automatically expands and contracts with signal strength and market conditions.&#x20;

* Typically around 30% of capital is exposed on average.
* Allocation expands only in strong-signal regimes.
* In weak-signal regimes most capital is held in cash or interest-bearing instruments.&#x20;

This structure is the strategy's first margin of safety: under a market shock, partial rather than full exposure limits losses.

### Venues

**Traditional:** Nasdaq, NYSE

**Centralized:** Binance

### **Asset universe**

The most liquid ETFs and equity index futures listed on the Nasdaq. The universe is structured to expand with market conditions and alpha validation.

#### **Liquidity and capacity**&#x20;

The strategy's underlying assets trade in some of the world's deepest liquidity pools, and every entry and exit size is small relative to market depth. Because the strategy does not depend on micro-alpha or capacity-bound inefficiencies, alpha decay with AUM growth is structurally small. Some sector ETFs are relatively shallow, so the strategy operates within a manageable capacity range and adjusts its instrument mix as scale grows.

## Risk Factors

**Directional and market risk.** The strategy carries directional long exposure and can lose money in a sustained, structural bear market in US equities. Its partial average exposure (around 30%) and regime-based entry control are designed to limit losses under market stress but do not remove directional exposure.

**Drawdown risk.** Layered risk controls are designed to keep deep drawdowns infrequent, but drawdowns cannot be eliminated.

**Leverage and derivative risk.** Where the strategy uses leveraged or derivative instruments (leveraged ETFs or index futures), additional risks apply, such as margin and daily-reset decay, which the strategy is designed around but does not eliminate.

**Smart contract risk.** Deposits, withdrawals, and vault accounting run through on-chain smart contracts, which carry inherent risk that cannot be eliminated entirely.

## Risk Management

The strategy's primary objective is minimizing drawdown, not maximizing return, and it targets a single-digit average drawdown. Risk is controlled through three layers:

* **Regime-based entry control.** Each asset builds positions only within a pre-defined regime. This is the most powerful drawdown-reduction mechanism, keeping the strategy out of the worst historical stretches of the underlying.
* **Conservative cross-asset sizing.** The most liquid ETFs tend to fall together under market stress. Rather than assuming diversification, the strategy sizes under the conservative assumption that they decline together.
* **Partial exposure.** Since only around 30% of capital is exposed on average, a market shock structurally limits losses relative to full exposure.

## Custody & Security

For positions on centralised exchanges, we use Copper (ClearLoop) and Ceffu (MirrorX), institutional off-exchange settlement providers, reducing exposure to exchange-level insolvency.

On-chain vault infrastructure, covering deposits, withdrawals, and on-chain operations, operates under the Neutral Strategy Vaults standard multi-party approval framework. Full details: [Security](https://docs.neutral.trade/vault-infrastructure/security).
