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

# JLP Delta Neutral Enhanced

## **Overview**

The JLP Delta Neutral Enhanced vault earns yield from Jupiter's JLP liquidity provision while systematically hedging all directional exposure to SOL, BTC, and ETH. Net delta is continuously targeting zero, returns are driven by JLP trading fees and borrowing fees, not by price direction.

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies/jlpdn">https://www.neutral.trade/strategies/jlpdn</a></td></tr></tbody></table>

## **How it works**&#x20;

### **Leveraging JLP**

JLP is Jupiter's liquidity provider token, earning 75% of all Jupiter Perps platform fees, opening and closing fees, price impact, trading fees, and borrowing fees.

The vault amplifies this yield through a looping process:

1. USDC deposits are used to mint JLP via the Jupiter Perps Program
2. JLP is deposited as collateral in [Jupiter JLP Loans](https://jup.ag/perps/jlp-loans)
3. USDC is borrowed against that collateral and used to acquire more JLP

<figure><img src="../../.gitbook/assets/aclev.png" alt=""><figcaption></figcaption></figure>

### **Delta Neutral Hedging**

JLP holds exposure to SOL, BTC, and ETH, through its token composition, and trader PnL. An automated hedging engine neutralises this:

1. Borrowed USDC is sent to Ceffu custody and mirrored to a Binance sub-account co-managed by Jupiter and Neutral Trade
2. JLP directional exposures are continuously monitored
3. Perpetual futures short positions are opened on Binance to offset exposure
4. Hedge weights adjust dynamically based on JLP composition and market conditions

<figure><img src="../../.gitbook/assets/alldat1.png" alt=""><figcaption></figcaption></figure>

## Yield Sources

* **JLP native yield** — 75% of all Jupiter Perps platform fees
* **Leverage amplification** — the looping structure increases effective yield relative to an unlevered position
* **Funding rates** — hedging position funding rates may add yield depending on market conditions; they can also be a cost

## Risk Factors

**JLP token risk** — JLP's market price may fluctuate relative to its virtual price during fast-moving markets. Rebalancing the hedge also incurs costs that create a threshold below which full delta-neutrality is not maintained.

**Exchange and settlement risk** — Hedging positions are held on Binance. Liquidity, market dislocation, and ADL risks apply. Centralized exchange custody risk is mitigated by Ceffu off-exchange custody/settlement. Collateral isn't held on Binance's balance sheet.

**Operational risk** — Off-chain delta calculations and daily PnL settlement between Ceffu and the on-chain vault are operational dependencies, managed under Neutral Strategy Vaults multi-party approval framework.

**Smart contract risk**

## Custody & Security

The vault operates under Neutral Strategy Vaults standard walled garden framework. Multi-party approvals for all fund movements, whitelisted addresses only, and no single key holder able to act unilaterally. Collateral held in Ceffu MPC custody and never on exchange balance sheets.&#x20;

Vault infrastructure has been audited by Quantstamp, Halborn, and Offside Labs. Full details: [Security](https://docs.neutral.trade/vault-infrastructure/security).
