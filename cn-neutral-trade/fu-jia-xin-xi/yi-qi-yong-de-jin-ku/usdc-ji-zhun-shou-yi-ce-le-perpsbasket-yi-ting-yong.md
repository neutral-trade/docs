---
description: USDC基准收益策略已取得显著成功，成为在牛市与熊市中均可稳定获利的卓越策略。
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/6YjCIQB3ardoMeqGMIF8/for-capital-allocators/deprecated-vaults/usdc-basis-perpsbasket-deprecated
---

# 🧺 USDC 基准收益策略（PerpsBasket）-【已停用】

<figure><img src="../../.gitbook/assets/123.png" alt=""><figcaption></figcaption></figure>

本策略将这套成功法则运用于多元化的资产组合，以提升稳定性并挖掘增长潜力。

通过这一新产品，我们拓展了久经验证的 USDC 基准收益策略的应用范围。USDC 基准收益策略（PerpsBasket）通过将资金分散至多种资产，显著增强了策略的抗风险能力，同时持续提供可观回报。

## **为什么选择 USDC 基准收益策略？** <a href="#id-2a94" id="id-2a94"></a>

本策略**堪称收益引擎**，能够每小时持续创造稳定回报。与众多策略不同，它在所有市场环境中均表现卓越。无论牛市或熊市，USDC 基准收益策略皆能以精准操作和低风险特性捕捉套利机会。

<figure><img src="https://cdn-images-1.medium.com/max/800/1*v1vXnQaMHaHAYLbw6QhFww.jpeg" alt=""><figcaption></figcaption></figure>

该策略的核心在于捕捉资金费率定价偏差。以**分析 Drift 上 SOL-PERP 资金费率为例，**&#x53EF;见以下显著数据：

* **过去一年中 91.5%** 的时间资金费率为正
* **年均资金费率收益达 30%**

通过套利不同资产间的资金费率差异，本策略不仅提供持续收益，还借助动态对冲有效降低整体风险。

<figure><img src="https://cdn-images-1.medium.com/max/800/1*NgUIq2o-cVAOthJjWl2bXQ.png" alt=""><figcaption><p>Strategy backtest for SOL-PERP on Drift</p></figcaption></figure>

## **运作机制简析**

:**基差交易的核心**在于捕捉资产**现货价格**与**期货价格**之间的差异。在 USDC 基准收益策略中，具体操作为：

* **在 Drift 上做空多个高流动性永续合约**
* **动态建立现货多头头寸**

通过这一组合操作，策略借助资金费率获取稳健且持续的收益。

<figure><img src="https://cdn-images-1.medium.com/max/800/1*KYaWWsF4u5sk_6BQRNfU6A.png" alt=""><figcaption></figcaption></figure>

**执行逻辑：**

* _资金费率为正时：_&#x5EFA;立基差头寸
* _资金费率连续 5 天为负时：_&#x53CD;转基差头寸方向

该策略通过动态对冲与多元配置，确保适应不同市场环境。借助灵活调整与资金费率分析，在有效控制风险的同时追求收益最大化。

## **费用与赎回规则**

本策略金库**免收服务费与绩效佣金。**

资金赎回设有 **1天** 的短期锁定期。

## 交易查询入口 (Drift)

{% hint style="info" %}
[https://app.drift.trade/?authority=4cvgasNfbJ36yeMVJSkscgL2Yco9dFGdj52Wrg91fmHv](https://app.drift.trade/?authority=4cvgasNfbJ36yeMVJSkscgL2Yco9dFGdj52Wrg91fmHv)
{% endhint %}

## 存入链接:

Neutral Trade 官网 (主要入口):

{% hint style="info" %}
[https://www.app.neutral.trade/strategies/perpsbasket](https://www.app.neutral.trade/strategies/perpsbasket)
{% endhint %}

Drift 官网 (次要入口):

{% hint style="info" %}
[https://app.drift.trade/vaults/strategy-vaults/4cvgasNfbJ36yeMVJSkscgL2Yco9dFGdj52Wrg91fmHv](https://app.drift.trade/vaults/strategy-vaults/4cvgasNfbJ36yeMVJSkscgL2Yco9dFGdj52Wrg91fmHv)
{% endhint %}

***

USDC Basis (Perps Basket) 启用日期 - 2024-12-09
