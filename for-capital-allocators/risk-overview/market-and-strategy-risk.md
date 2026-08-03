---
description: Why market neutral does not mean risk-free, and how strategies can lose money.
---

# Market & Strategy Risk

Every vault on Neutral Trade is an active trading strategy. Returns come from real market sources — funding rates, price spreads between venues, volatility premia, or directional signals — and each of those sources can stop paying, or reverse, at any time. This page explains how strategies lose money, so you can judge whether a strategy's risk profile fits your own.

{% hint style="warning" %}
Market neutral means a strategy hedges directional price exposure — it is not positioned to profit or lose simply because the market goes up or down. It does not mean the strategy cannot lose money.
{% endhint %}

### How Market Neutral Strategies Lose Money

**Basis and spread risk.** Strategies that trade the gap between two related prices — spot versus perpetual, one venue versus another — profit when that gap converges. Gaps can widen before they converge, and can stay dislocated longer than a position can be economically held.

**Funding rate reversal.** Funding-rate strategies collect payments while funding is positive. Funding can flip negative and remain negative for extended periods, turning a yield source into a running cost.

**Execution risk.** Hedged strategies hold at least two legs. When legs fill at different times or prices — which is most likely in fast markets — the strategy briefly carries the exposure it was designed to avoid, and slippage eats into the spread being captured.

**Liquidity risk.** Displayed order-book depth is not committed capital. In stressed conditions, liquidity tends to disappear from all venues at once — exactly when a strategy most needs to adjust or exit positions.

**Leverage.** Some strategies use leverage to make thin spreads economic. Leverage amplifies every one of the risks above, and adds liquidation risk if collateral values move sharply.

**Model and data risk.** Strategies run on automated systems fed by market data. Stale prices, venue outages, or model assumptions that stop holding can produce losses before a human intervenes.

### Directional Strategies Are Different

CTA and momentum-based vaults take deliberate market exposure — that is the strategy. Drawdowns are an expected part of their return profile, not a malfunction: these strategies typically lose small amounts repeatedly while waiting for the large moves that drive their returns. Review each vault's maximum drawdown and volatility figures, and treat them as a preview of what holding the strategy through a bad stretch feels like.

### What Mitigates These Risks

Every curator passes our [vetting framework](../../curators/copy-of-strategy-curator-vetting-framework.md) before managing capital, which scores risk management — leverage limits, daily loss thresholds, drawdown response procedures, and position concentration caps — as a heavily weighted dimension. Curators report positions through API access, and vault-level guardrails ([bounded NAV updates, the liquidity reserve, and the emergency circuit breaker](../../neutral-strategy-vaults/vault-protections.md)) contain the damage an anomaly can do. Allocating across strategies — directly or through Neutral Autopilot — reduces dependence on any single strategy's performance.

### What Remains

None of the above guarantees that a spread converges, that a hedge stays available, or that an exit completes at the expected price. Published metrics — APY, Sharpe ratio, maximum drawdown — are historical measurements, not forecasts; see [APY and APR Calculations](../../additional-info/apy-and-apr-calculations.md) for how they are computed. Past performance does not indicate future results, and a strategy with years of steady returns can still have its worst month next month.
