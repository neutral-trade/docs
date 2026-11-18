---
description: 数学逻辑确凿无疑！
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/6YjCIQB3ardoMeqGMIF8/for-capital-allocators/deprecated-vaults/inverse-jlp-dn-deprecated
---

# 📉 反向 JLP Delta 中性策略 -【已停用】

<figure><img src="../../.gitbook/assets/123.png" alt=""><figcaption></figcaption></figure>

在 Drift 协议中，随着从 JLP 本身获取收益的 Delta 中性策略不断扩展，未平仓合约（OI）逐渐偏向空头。这主要是由于此类策略普遍利用永续合约空头来对冲其 JLP 多头持仓。那么，是否存在一种方式能在这样的市场结构中从 OI 偏向中获利呢？

**“大空头”金库——反向 JLP Delta 中性策略应运而生！**

该策略通过抵押 USDC、借助借贷市场做空 JLP，并利用永续合约多头对冲 JLP 底层波动资产及交易员盈亏风险，在保持 Delta 中性的框架内实现收益捕获。当资金费率为负时，策略不仅通过 USDC 借贷头寸赚取收益，还可凭借永续多头头寸获取负资金费率带来的正向收益。

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcipHI0bwDs8Qwv8Q06KPL4hbK1vOOzOttjMjrLzGOMdQxpqUBGqmI93-vg5Cvs_daB79bqjawvkiuyL4Gjh00qNsFFmTGV2Dh2P-g65afy9gMt8v9r3m6ruUcBAZ7M-Ot8JiSL?key=elNUG_Xyzz7tnmzIfOxqAgGY" alt=""><figcaption></figcaption></figure>

依托 Drift 与 Jupiter 的双重优势，本策略致力于在市场不确定性中提供稳定收益。传统永续空头结构的 Delta 中性策略因资金费率影响导致收益缩水？

**这在本策略中将不复存在！**

通过**大空头**反向 JLP Delta 中性金库，您可在当前市场环境下依然获得持续可观收益。

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfnp6A2L9RiEBmHYhtKUh-CAuYVSa5KoSngOvI7O6ufwGdF-Wgy5AbyZnDnkXTXNVdzuGIpB4A-KMyUliQ02KoGh5MyPONeOv54cUKnMZUYYR0zCp8kac7qdD2uXUDd9-4vE9ML_A?key=elNUG_Xyzz7tnmzIfOxqAgGY" alt=""><figcaption></figcaption></figure>

## **费用与赎回规则**

**绩效佣金**：从本策略为您实现的收益中抽取 **20%。**

**赎回锁定期**：为优化流动性管理与策略收益，设有 **1天** 的短期锁定期。

## 风险提示

{% embed url="https://neutraltrade.medium.com/risks-of-the-jlp-delta-neutral-strategy-294d0899ece4" %}

***

启用日期: 2025-02-15
