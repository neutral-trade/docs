---
description: 您的资金安全，始终是首要优先级。
---

# 安全机制

Neutral Trade 的安全体系分为三个层次：经审计的智能合约基础设施、针对中心化交易所仓位的机构级场外托管，以及防止任何单一方单方面行动的运营控制。

***

### 智能合约审计

支撑 Neutral Trade 所有策略的金库基础设施（Neutral Strategy Vaults）已由三家安全机构独立审计，报告均已公开。

| 审计机构             | 日期               | 审计范围                 | 报告                                                                                                            |
| ---------------- | ---------------- | -------------------- | ------------------------------------------------------------------------------------------------------------- |
| **Halborn**      | 2025 年 1 月 21 日  | Neutral Trade 金库基础设施 | [查看报告](https://www.halborn.com/audits/neutral-trade/neutral-trade---smart-contract-assessment-0777aa)         |
| **Quantstamp**   | 2025 年 6 月 25 日  | Neutral Trade 金库基础设施 | [查看证书](https://certificate.quantstamp.com/full/neutral-trade/52a6403b-648c-4ea6-be5e-c8b525acc9b7/index.html) |
| **Offside Labs** | 2025 年 12 月 11 日 | Neutral Trade 金库基础设施 | [查看报告](https://drive.google.com/file/d/11Ck5gkVXLot_se_hxPRWUU_FT_vjsrar/view?usp=sharing)                    |

审计会评估代码中的漏洞、经济模型设计缺陷与非预期行为，但并不能消除所有风险。完整披露请参阅[《风险提示与免责声明》](../faltiao-kuan/feng-xian-ti-shi-yu-mian-ze-sheng-ming.md)。

### 机构级托管

您的资产如何保管，取决于策略在何处执行。

**链上仓位 — Fordefi MPC**

对于所有链上金库操作与 Solana 端的管理，Neutral Trade 使用机构级 MPC（多方安全计算）钱包基础设施 [Fordefi](https://fordefi.com)。这可以保护 Neutral Strategy Vaults 及所有链上资金转移，免受外部攻击与内部滥用。

**中心化交易所仓位 — Copper 与 Ceffu**

对于在中心化交易所执行的策略，Neutral Trade 使用 [Copper](https://copper.co)（ClearLoop）与 [Ceffu](https://ceffu.com)（MirrorX）提供场外托管与结算。

Copper 与 Ceffu 的托管仅适用于含中心化交易所执行环节的策略。

***

### 运营安全

**多方审批** 关键操作（包括金库配置变更、新地址白名单与策略更新）均需多名授权团队成员审批。任何单一个人都无法对用户资金单方面行动。

**最小权限原则** 团队成员仅可访问其职责所需的系统。访问权限会定期审阅，并在不再需要时及时撤销。

***

### 金库层面的保护

除托管与审计之外，金库智能合约本身也内置了多项保护：受限制的净值更新（抵御价格操纵）、交易批处理（防范 MEV 套利）、每项费用参数的硬上限、参数变更的 12 小时时间锁，以及存取款的暂停机制（熔断器）。参数变更还需另行经过多方审批（见上文“运营安全”）。这些机制在[《金库安全机制》](jin-ku-an-quan-ji-zhi.md)页面中以通俗语言说明。

***

### 风险披露

尽管我们采取一切预防措施保护您的资金，但任何安全体系都无法消除全部风险。请务必理解，投资 DeFi 具有固有风险。存入前请认真阅读我们的[《风险提示与免责声明》](../faltiao-kuan/feng-xian-ti-shi-yu-mian-ze-sheng-ming.md)。

***

_Neutral Trade – 构建收益的未来_
