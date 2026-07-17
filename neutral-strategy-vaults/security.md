---
description: Your Funds. Our Priority.
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

# Security

Neutral Trade's security approach operates across three layers: audited smart contract infrastructure, institutional custody for off-exchange CEX positions, and operational controls that prevent unilateral action by any single party.

***

### Smart Contract Audits

The vault infrastructure (Neutral Strategy Vaults) underpinning all Neutral Trade strategies has been independently audited by three security firms. Reports are publicly available.

| Auditor          | Date              | Scope                               | Report                                                                                                                    |
| ---------------- | ----------------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **Halborn**      | January 21, 2025  | Neutral Trade Vaults Infrastructure | [View Report](https://www.halborn.com/audits/neutral-trade/neutral-trade---smart-contract-assessment-0777aa)              |
| **Quantstamp**   | June 25, 2025     | Neutral Trade Vaults Infrastructure | [View Certificate](https://certificate.quantstamp.com/full/neutral-trade/52a6403b-648c-4ea6-be5e-c8b525acc9b7/index.html) |
| **Offside Labs** | December 11, 2025 | Neutral Trade Vaults Infrastructure | [View Report](https://drive.google.com/file/d/11Ck5gkVXLot_se_hxPRWUU_FT_vjsrar/view?usp=sharing)                         |

Audits assess code for vulnerabilities, economic design flaws, and unintended behaviours. They do not eliminate all risk, see [Risk Warnings and Disclaimers](../legal/risk-warnings-and-disclaimers-statement.md) for a full disclosure.

### Institutional-Grade Custody

How your assets are held depends on where the strategy executes.

**On-chain positions — Fordefi MPC**

For all on-chain vault operations and Solana-side management, Neutral Trade uses [Fordefi](https://fordefi.com), an institutional MPC (Multi-Party Computation) wallet infrastructure.This protects the Neutral Strategy Vaults and all on-chain capital movements from both external attack and internal misuse.

**Centralised exchange positions — Copper and Ceffu**

For strategies that execute on centralised exchanges, Neutral Trade uses [Copper](https://copper.co) (ClearLoop) and [Ceffu](https://ceffu.com) (MirrorX) for off-exchange custody and settlement.&#x20;

Copper and Ceffu custody applies only to strategies with centralised exchange execution legs.

***

### Operational Security

**Multi-party approvals** Critical operations, including vault configuration changes, whitelisting new addresses, and policy updates, require approval from multiple authorised team members. No single individual can take unilateral action on user funds.

**Least privilege access** Team members have access only to the systems required for their role. Access is reviewed regularly and revoked when no longer needed.

***

### Vault-Level Protections

Beyond custody and audits, the vault smart contracts themselves include several built-in protections. NAV manipulation controls, transaction batching to prevent MEV exploitation, a 24-hour timelock on parameter changes, and an emergency circuit breaker. These are explained in plain language on the [Vault Protections](https://docs.neutral.trade/vault-infrastructure/vault-protections) page.

***

### Risk Disclosures

While we take every precaution to protect your funds, no security framework eliminates all risk. It is important to understand that investing in DeFi carries inherent risks. Please read our [Risk Warnings and Disclaimers Statement](../legal/risk-warnings-and-disclaimers-statement.md) carefully before depositing.

***

_Neutral Trade – Building the Future of Yield_
