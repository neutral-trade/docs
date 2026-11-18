---
description: >-
  How Neutral Trade protects deposits: four independent audits, custody with
  Fordefi, Copper and Ceffu, and multi-party controls.
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
  anchors:
    visible: true
---

# Security

Neutral Trade's security approach operates across three layers: audited smart contract infrastructure, institutional custody for off-exchange positions, and operational controls that prevent unilateral action by any single party.

***

## Smart Contract Audits

The Solana vault program behind Neutral Strategy Vaults has been independently audited by four security firms. All four reports are public.

| Auditor          | Date              | Scope                               | Report                                                                                                                    |
| ---------------- | ----------------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **Halborn**      | January 21, 2025  | Neutral Trade Vaults Infrastructure | [View Report](https://www.halborn.com/audits/neutral-trade/neutral-trade---smart-contract-assessment-0777aa)              |
| **Quantstamp**   | June 25, 2025     | Neutral Trade Vaults Infrastructure | [View Certificate](https://certificate.quantstamp.com/full/neutral-trade/52a6403b-648c-4ea6-be5e-c8b525acc9b7/index.html) |
| **Offside Labs** | December 11, 2025 | Neutral Trade Vaults Infrastructure | [View Report](https://drive.google.com/file/d/11Ck5gkVXLot_se_hxPRWUU_FT_vjsrar/view?usp=sharing)                         |
| **Adevar Labs**  | October 3, 2026   | Neutral Trade Vaults Infrastructure | [View Report (PDF)](../.gitbook/assets/neutral-trade-adevar-labs-audit-report-2026-10.pdf)                                |

The most recent audit, by Adevar Labs, found no Critical issues. Every High and Medium finding was fixed and verified in the fix review. You can view and download the full report here:

{% file src="../.gitbook/assets/neutral-trade-adevar-labs-audit-report-2026-10.pdf" %}
Adevar Labs audit report, after fix review (October 3, 2026)
{% endfile %}

Audits assess code for vulnerabilities, economic design flaws, and unintended behaviours. They do not eliminate all risk. See [Risk Warnings and Disclaimers](../legal/risk-warnings-and-disclaimers-statement.md) for a full disclosure.

## Institutional-Grade Custody

How your assets are held depends on where the strategy executes.

**On-chain positions: Fordefi MPC**

For all on-chain vault operations and Solana-side management, Neutral Trade uses [Fordefi](https://fordefi.com), an institutional MPC (Multi-Party Computation) wallet infrastructure. This protects the Neutral Strategy Vaults and all on-chain capital movements from both external attack and internal misuse.

**Centralized exchange positions: Copper and Ceffu**

For strategies that execute on centralized exchanges, Neutral Trade uses [Copper](https://copper.co) (ClearLoop) and [Ceffu](https://ceffu.com) (MirrorX) for off-exchange custody and settlement. Capital stays with the custodian and is mirrored to the exchange, which reduces exposure to an exchange failure.

Copper and Ceffu custody applies only to strategies with centralized exchange execution legs. The [venue, counterparty and curator risk](../for-capital-allocators/risk-overview/venue-counterparty-and-curator-risk.md) page maps each custody route.

## Trading Firms Can Trade. They Cannot Withdraw.

A curator receives execution permissions only. Vault capital cannot be sent to an arbitrary external address, by the curator or by Neutral Trade. Every movement is restricted to pre-approved addresses, contracts, and custody routes.

## Operational Security

**Multi-party approvals.** Critical operations, including vault configuration changes, whitelisting new addresses, and policy updates, require approval from multiple authorised team members. No single individual can take unilateral action on user funds.

**Least privilege access.** Team members have access only to the systems required for their role. Access is reviewed regularly and revoked when no longer needed.

## Vault-Level Protections

Beyond custody and audits, the vault smart contracts themselves include several built-in protections: bounded NAV updates to resist price manipulation, transaction batching to prevent MEV exploitation, hard caps on every fee parameter, a 12-hour timelock on parameter changes, and a pause (circuit breaker) on deposits and withdrawals. Parameter changes are additionally subject to multi-party approval. These are explained in plain language on the [Vault Protections](vault-protections.md) page.

## Vaults on Other Networks

The four audits above cover the Solana vault program. Vaults that accept deposits on other networks use a separate vault contract on that network. Today these are Neutral Autopilot on Ethereum and Meridian Liquidity Provider on Robinhood Chain. The vault's Details view in the app names the network and the contract.

## Common Questions

**Has Neutral Trade been audited?**

Yes. Halborn, Quantstamp, Offside Labs, and Adevar Labs have each audited the vault program. The most recent audit is dated October 3, 2026.

**Can a trading firm withdraw my deposit?**

No. Curators have execution permissions only. Fund movements are restricted to pre-approved addresses.

**Who holds the assets?**

On-chain assets sit in the vault program and Fordefi MPC wallets. Centralized exchange collateral sits in off-exchange custody with Copper or Ceffu.

## Risk Disclosures

While we take every precaution to protect your funds, no security framework eliminates all risk. Read the [Risk Overview](../for-capital-allocators/risk-overview/) and the [Risk Warnings and Disclaimers Statement](../legal/risk-warnings-and-disclaimers-statement.md) before depositing.
