---
description: 中频做市策略 Mid-Frequency Market Making
---

# 中频做市策略

## 概览

这是一套中频做市策略，通过为 Binance 永续合约市场提供流动性来获取稳定收益。系统会根据当前市况持续调整报价与报单活跃度。超额收益既来自自研公允价格模型的预测能力，也来自高质量的交易执行能力。当风险上升时，策略会主动收缩以保护本金。

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>存入</strong></td><td><a href="https://www.neutral.trade/strategies/adverseguard-alpha">https://www.neutral.trade/strategies/adverseguard-alpha</a></td></tr></tbody></table>

_自 2026 年 4 月 23 日起上线_

## 运作方式

**价差捕获** — 系统在 Binance 的 ETHUSDT 永续合约订单簿上持续双边报价。通过维持活跃的买卖报价，策略赚取买卖价差并获得 Maker 返佣。

**公允价格模型** — 策略核心是一套自研模型，可实时估算 ETHUSDT 的真实公允价格。策略以该公允价格（而非当前价差的中位价）为基准布置报价，从而提升每笔成交的盈利水平。

**逆向选择检测** — 第二套预测模型持续监控大额方向性行情即将到来的迹象，并识别逆向选择——即在重大价格变动中站在错误一方的风险。一旦这些信号触发，报价活动会自动收缩或暂停，直至市况恢复正常。

最终形成一种非对称的收益特征：市况平稳时持续获取价差收入，市况恶化时则自动收缩。

#### 交易场所

**中心化交易所：** Binance

### 收益来源

* 买卖价差
* Maker 返佣
* 短期市场无效性

![](https://15023324-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FTBbIFSVhH4bZpN1NJyUi%2Fuploads%2FtoDrAFalMxJdgp6wVFHJ%2Fcumulative_return_1_5x_realized.png?alt=media\&token=794b4e04-d39b-408a-9ec3-4fea719f3431)

## 风险管理

策略采用一套止损框架，旨在同时在执行层面与组合层面控制风险。

**交易系统控制** 第一层直接运行在交易程序内部，实时监控仓位敞口，并在策略层面触发自动止损，在亏损累积之前应对不利价格变动。

**回撤情况** 历史最大观测回撤为 -5.42%，发生于去年 10 月 10 日。此后策略未再突破该水平。

**动态风险缩放** 除止损控制之外，策略的预测模型会持续监控逆向选择与方向性风险。当风险条件升高时，报价活动会自动收缩或暂停，优先保全本金，而非追逐边际价差收入。

## 为什么选择 AdverseGuard Alpha？

AdverseGuard Alpha 游走于传统金融与数字资产的交叉地带，在全球市场部署多策略量化框架。

其优势建立在一支世界级团队之上，团队在高频交易、资产管理与交易所基础设施领域根基深厚，拥有来自 Tower Research、Citadel、Susquehanna（SIG）、Kronos Research、Point72、State Street、RBC 与摩根大通等行业巨头的数十年累计机构经验。这一机构背景使其能够弥合传统金融的严谨性与数字资产流动性前沿之间的鸿沟。

{% hint style="info" %}
为避免策略信息泄露，我们未公开 AdverseGuard Alpha 的完整名称。Neutral Trade 已完成充分的尽职调查，包括真实资金测试。
{% endhint %}
