---
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

# Cross-Exchange Arb

## Overview

The Cross-Exchange Arb Vault is designed to generate stable, risk-controlled yield by deploying market-neutral strategies that monetize structural inefficiencies in crypto markets. Powered by Hyperithm, the vault operates on a delta-neutral basis, aiming to minimize directional exposure to underlying asset price movements while capturing non-directional sources of return.

Capital is dynamically allocated based on expected yield, execution costs, and margin efficiency. Hedging positions are monitored and rebalanced continuously to maintain minimal net delta exposure, with leverage and position sizing adjusted systematically in response to changing market conditions.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies/hyperithm1">https://www.neutral.trade/strategies/hyperithm1</a></td></tr></tbody></table>

_Live since January 2026_

## How it works

Funding rates on perpetual futures markets frequently diverge across venues. When one exchange's perpetual is trading at a significant premium to another,  the strategy exploits the differential, earning the spread while remaining market-neutral.

The strategy operates across a dynamically selected universe of assets and exchanges (decentralized, centralized, and traditional) where opportunities are present. Asset selection and position sizing are governed by real-time monitoring of funding rates, borrow rates, and margin efficiency across all active venues.

#### **Venues**

**Decentralized:** Lighter, Hyperliquid

**Centralized:** OKX, Binance, Gate, Bybit

**Traditional:** CME, Nasdaq, NYSE

### Yield Sources

* **Perpetual funding payments**&#x20;
* **Spot-perp price inefficiencies**
* **Borrow rate differentials**

## Risk Factors

**Liquidation and ADL risk** — Extreme price movements can trigger forced liquidation or Auto-Deleveraging on futures venues, even with delta-neutral positioning. Mitigation: constant position rebalancing to manage ADL rank and cross-margin interaction monitoring.

**Funding rate risk** — Funding rates can compress, turn negative, or shift regime rapidly. Mitigation: The strategy monitors rates continuously and adjusts positions when net expected yield no longer justifies execution costs or margin usage. The system is designed to adapt to crowding dynamics.

**Counterparty and operational risk** — **Counterparty and exchange risk** — Exposure to venue-level failure, insolvency, or operational disruption. Mitigations include: Off-exchange custody and settlement via Ceffu (MirrorX) for centralised exchange trading.

**Operational risk** — Multi-venue, multi-strategy execution depends on the continuous availability of trading infrastructure, exchange APIs, and custody integrations. Disruption at any layer can prevent timely rebalancing.

**Smart contract risk**

## Custody & Security

For centralised exchange trading, Copper (ClearLoop) and Ceffu (MirrorX) are used for institutional off-exchange custody/settlement.&#x20;

On-chain vault infrastructure, covering deposits, withdrawals, and onchain operations, operates under Neutral Strategy Vaults standard multi-party approval framework, independent of the centralised exchange custody arrangements. Full details: [Security](https://docs.neutral.trade/vault-infrastructure/security).
