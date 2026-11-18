---
description: 专为 JLP 持有者打造的稳健收益理想解决方案。
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/6YjCIQB3ardoMeqGMIF8/for-capital-allocators/deprecated-vaults/jlp-delta-neutral-on-drift-deprecated/jlp-delta-neutral-on-drift-jlp-in-kind-deprecated
---

# JLP DN on Drift 策略（JLP 原生存入）-【已停用】

## 策略详解

Neutralized JLP 为 JLP 持有者带来显著的短、中、长期收益。存入 JLP，即可在对冲市场风险的同时，赚取 Jupiter 永续合约的交易手续费。本策略与我们 USDC 质押版（JLP Delta Neutral）策略内核完全一致，仅计价单位改为 JLP，并采用管理费模式，不收取绩效分成。

但尽管该策略内核与 USDC 计价版相同，但 **JLP 作为计价单位改变了一些细节，并拓展了其应用场景。**

**让我们来详细了解 JLP DN (JLP 本位) 策略！**

<figure><img src="../../../.gitbook/assets/JLP price movements(5).svg" alt=""><figcaption></figcaption></figure>

## JLP 本位**策略差异解析**

**首先，请观察上图示意。**

在此金库中，您持有的 **JLP 数量会随 JLP 价格波动而变化。**

尽管JLP数量可能因价格涨跌而增减，但您仓位的 USDC 估值将保持稳定（同时您仍能获取 Jupiter 永续合约的手续费收益）。

### 潜在应用场景:

由于本策略金库以 JLP 计价，您可主动利用此特性捕捉 JLP 的价格波动机会！

#### **市场看跌情绪弥漫？**

* **立即存入**：在JLP价格下行时积累更多份额。

#### **触及阶段性底部，转而看涨？**

* **果断赎回**：以高于初始的JLP持仓重新获得方向性敞口！

赎回流程仅有 1 小时的锁定期，让您的资金规划保有充分弹性。

## 策略设计

尽管本策略以JLP计价，但其执行的仍为相同的JLP Delta中性策略内核。

如需了解此策略的设计详情，请参阅以下内容：

{% hint style="info" %}
[https://docs.neutral.trade/main-products/quant-strategies/market-neutral/jlp-delta-neutral-usdc](https://docs.neutral.trade/main-products/quant-strategies/market-neutral/jlp-delta-neutral-usdc)
{% endhint %}

### 费用与赎回规则

* **服务费**：7%（根据资金在库内的存续时长按比例计提）
* **赎回锁定期**：1小时

## 存入链接

Neutral Trade 官网 (主入口):

{% hint style="info" %}
[https://www.app.neutral.trade/strategies/neutralizedjlp](https://www.app.neutral.trade/strategies/neutralizedjlp)
{% endhint %}

Drift 官网 (备选入口):

{% hint style="info" %}
[https://app.drift.trade/vaults/strategy-vaults/CG2zv4wsSetgs6mAucEKnHPwSoZSLYMwGroembTUNeaU](https://app.drift.trade/vaults/strategy-vaults/CG2zv4wsSetgs6mAucEKnHPwSoZSLYMwGroembTUNeaU)
{% endhint %}

### **交易查询入口** (Drift)

{% hint style="info" %}
[https://app.drift.trade/?authority=CG2zv4wsSetgs6mAucEKnHPwSoZSLYMwGroembTUNeaU](https://app.drift.trade/?authority=CG2zv4wsSetgs6mAucEKnHPwSoZSLYMwGroembTUNeaU)
{% endhint %}

***

## 风险提示

{% embed url="https://neutraltrade.medium.com/risks-of-the-jlp-delta-neutral-strategy-294d0899ece4" %}

***

Launch date: 2025-02-13&#x20;
