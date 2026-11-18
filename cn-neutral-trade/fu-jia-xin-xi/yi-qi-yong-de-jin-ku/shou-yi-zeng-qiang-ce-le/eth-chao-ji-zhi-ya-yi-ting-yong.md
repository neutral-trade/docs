---
description: 加密领域中最高的 ETH 真实收益策略。
icon: ethereum
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/6YjCIQB3ardoMeqGMIF8/for-capital-allocators/deprecated-vaults/yield-enhancement/eth-super-staking-deprecated
---

# ETH 超级质押 -【已停用】

## ETH **超级质押策略解析**

ETH 超级质押为以太坊持有者提供了一套强大的流动性增强方案，不仅提升了用户资产效率，也增强了去中心化交易所（特别是Jupiter 永续合约DEX）的流动性深度。

我们通过获取并抵押 wETH，随后以此抵押品开设借贷头寸，在wETH基础上运行Delta中性策略，实现风险对冲后的稳健收益。

## **收益来源解析**

本质押金库的收益主要由以下两部分构成，使您在获得纯ETH敞口的同时，也能获取持续且稳定的回报：

1. **JLP手续费收益**\
   截至2025年9月12日，APY为**17.59%**\
   来源：Jupiter Perp DEX上交易者支付的交易费、借贷费、铸造/销毁费及清算费中的**75%**&#x5206;成
2. **永续空头资金费率收益**（多头通常向空头支付资金费用）\
   截至2025年9月19日各资产APR分别为：\
   ∙ ETH：约 **7.92%**\
   ∙ BTC：约 **11.20%**\
   ∙ SOL：约 **3.02%**

以上收益来源共同作用，使您在获得纯粹 ETH 敞口的同时，也能获取持续稳定的回报。

## **什么是 wETH？**

Wrapped Ethereum（wETH）是以太坊的代币化版本，可在以太坊、Solana等其他区块链上运行，并与以太坊价值保持1:1锚定。

wETH使ETH持有者无需出售原生资产即可参与各类DeFi应用，解锁了以太坊主网之外更广泛的协议访问与流动性选择。



## **传统 ETH 质押方案**

* 主流 DEX 纯 $ETH 质押收益：约 5% 年化
* 平台 ETH 借贷基础收益：约 2% 年化

ETH 超级质押旨在实现超额收益，其增强型回报是传统 ETH 质押方案无法比拟的。

## **锁定期与赎回规则**&#x20;

我们的 ETH 超级质押金库将收取 20% 的绩效佣金及 1% 的服务&#x8D39;**，**&#x4EE5;此确保激励一致。

为优化流动性管理并保障策略收益，用户赎回操作设有 1 天的短期锁定期。

## **与原始 JLP Delta 中性金库的风险对比**

除[此文档](https://neutraltrade.medium.com/risks-of-the-jlp-delta-neutral-strategy-294d0899ece4)所述的常规风险外，需特别注意的是：**本策略参与者需完全承担 $ETH 的市场波动风险**。这意味着您的损益将直接取决于 $ETH 的价格走势——可能获得上涨收益，也可能承担下跌损失。&#x20;

## 交易查询入口 (Drift)

{% hint style="info" %}
[https://app.drift.trade/?authority=ENr5e1BMN5vFUHf4iCCPzR4GjWCKgtHnQcdniRQqMdEL](https://app.drift.trade/?authority=ENr5e1BMN5vFUHf4iCCPzR4GjWCKgtHnQcdniRQqMdEL)
{% endhint %}

## 存入链接:

Neutral Trade 官网 (主要入口):

{% hint style="info" %}
[https://www.app.neutral.trade/strategies/ethnl](https://www.app.neutral.trade/strategies/ethnl)
{% endhint %}

Drift 官网 (备选入口):

{% hint style="info" %}
[https://app.drift.trade/vaults/strategy-vaults/ENr5e1BMN5vFUHf4iCCPzR4GjWCKgtHnQcdniRQqMdEL](https://app.drift.trade/vaults/strategy-vaults/ENr5e1BMN5vFUHf4iCCPzR4GjWCKgtHnQcdniRQqMdEL)
{% endhint %}

***

ETH 超级质押启用日期 - 2024-11-17
