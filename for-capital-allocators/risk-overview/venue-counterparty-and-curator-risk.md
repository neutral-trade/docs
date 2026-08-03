---
description: >-
  Where your capital sits while a strategy runs, and what a venue or
  counterparty failure would mean.
---

# Venue, Counterparty & Curator Risk

When you deposit into a vault, your capital does not sit idle in the vault contract. It is deployed to the venues where the strategy executes — DeFi protocols, decentralised exchanges, and for some strategies centralised exchanges, sometimes across multiple chains. While deployed, your capital is exposed to those venues and to the counterparties involved in running the strategy. This page explains where it sits and what a failure would mean.

### Where Your Capital Sits

**On-chain venues.** Capital deployed to Solana programs and other DeFi protocols is managed through [Fordefi](https://fordefi.com) MPC wallet infrastructure, with movements restricted to pre-approved contracts and venues.

**Centralised exchange legs.** Strategies that execute on centralised exchanges use off-exchange custody and settlement — [Copper](https://copper.co) (ClearLoop) and [Ceffu](https://ceffu.com) (MirrorX) — so that collateral is held with the custodian rather than deposited directly on the exchange.

{% hint style="warning" %}
Off-exchange custody reduces exchange counterparty exposure — it does not eliminate it. Open positions, unsettled profit and loss, and anything inside a settlement cycle still depend on the exchange's continued operation.
{% endhint %}

### Exchange Counterparty Risk

If a centralised exchange used by a strategy were to halt withdrawals or become insolvent, the capital at risk is the exposure inside the exchange at that moment: open positions and any value not yet settled back to custody. Off-exchange settlement keeps that exposure materially smaller than depositing directly on the exchange, and venue usage is monitored on an ongoing basis — but no monitoring can guarantee enough warning to exit a failing venue before it stops honouring obligations.

### External Protocol Risk

Strategies that deploy into DeFi protocols take on those protocols' own risks: smart contract exploits, oracle failures, and economic design flaws. The [audits](../../neutral-strategy-vaults/security.md) covering Neutral Strategy Vaults apply to our vault infrastructure — they do not extend to the external protocols a strategy interacts with. NT Earn, which allocates across Solana lending protocols, carries this risk as its primary exposure.

### Asset Risk

Vault deposit assets and strategy collateral are typically stablecoins. A stablecoin losing its peg — temporarily or permanently — would directly affect vault value, independent of how the strategy is performing. Issuer solvency and redemption mechanics differ by asset.

### Curator Risk

Curators — the trading firms managing strategies — operate under hard structural limits: they have API access to trade, but [no ability to withdraw or redirect user funds](../../neutral-strategy-vaults/vault-protections.md). What the structure cannot prevent is a curator trading badly, breaching its own risk discipline, or suffering an operational failure. Every curator is scored through the [Strategy Curator Vetting Framework](../../curators/copy-of-strategy-curator-vetting-framework.md) before onboarding — track record verification, risk management, team and operations, and legal standing — and monitored on an ongoing basis afterwards. Vetting raises the bar; it does not guarantee future performance or operational integrity.

### What a Failure Would Mean for You

In the worst case — an exchange insolvency or an external protocol exploit while a strategy has capital deployed there — the affected portion of the vault's capital could be partially or entirely lost, and the vault's share price would reflect that loss across all depositors in the vault. The [emergency circuit breaker](../../neutral-strategy-vaults/vault-protections.md) can recall deployed capital and halt flows to contain exposure, but it cannot recover value from a failed counterparty.

Counterparty risk is a real, priced-in part of what these strategies earn. Size your allocation on that basis, and read the [Risk Warnings and Disclaimers Statement](../../legal/risk-warnings-and-disclaimers-statement.md) for the full disclosure.
