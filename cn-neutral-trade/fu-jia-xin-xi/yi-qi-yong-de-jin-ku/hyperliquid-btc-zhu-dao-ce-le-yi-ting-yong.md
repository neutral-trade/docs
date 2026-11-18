---
icon: btc
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/6YjCIQB3ardoMeqGMIF8/for-capital-allocators/deprecated-vaults/hyperliquid-btc-dominance-deprecated
---

# \[Hyperliquid] BTC 主导策略 -【已停用】

<figure><img src="../../.gitbook/assets/123.png" alt=""><figcaption></figcaption></figure>

Neutral Trade 现已正式上线 Hyperliquid——首发推出我们的[资金费率套利策略](https://app.gitbook.com/o/8BrTz5uVFY2dUubyr6ic/s/TBbIFSVhH4bZpN1NJyUi/~/changes/1/zhu-yao-chan-pin/liang-hua-ce-le-mo-kuai/shi-chang-zhong-xing-ce-le/hyperliquid-zi-jin-feiltao-li-ce-le-usdc)，并同步上线两款全新的主导权金库，这些产品均直接构建于 Hyperliquid 原生金库基础设施之上。

{% hint style="info" %}
在 Hyperliquid 上享更多优惠！使用我们的推荐码：

[https://app.hyperliquid.xyz/join/NEUTRALTRADE](https://app.hyperliquid.xyz/join/NEUTRALTRADE)
{% endhint %}

<figure><img src="../../.gitbook/assets/Drafts for posting (dont delete) (38).png" alt=""><figcaption></figcaption></figure>

## 🤔 **什么是主导权？**

主导权反映了特定资&#x4EA7;**（比特币或山寨币）**&#x5728;整个加密市场总市值中所占的比例。

### ➗**计算公式：**

$$
\text{Dominance}_{BTC} = \frac{\text{Market Cap}_{BTC}}{\sum_{i=1}^{N} \text{Market Cap}_i}
$$

该比率反映资金流向：

* **BTC主导率上升** → 资金正涌入比特币（避险模式）
* **BTC主导率下降** → 资金正流向山寨币（风险偏好模式）

**山寨币主导率**即为其反向指标：

$$
\text{Dominance}_{ALT} = 1 - \text{Dominance}_{BTC}
$$

***

## 1. BTC **主导金库**

<figure><img src="../../.gitbook/assets/chrome_wwWD0Lp5tD.png" alt=""><figcaption></figcaption></figure>

该金库捕捉**比特币相对于山寨币的强势表现。**

策略配置：

* **做多 BTC**
* **做多在 Hyperliquid 上的多元化山寨币组合**

当比特币表现跑赢山寨币时即可获利——即使在横盘或下跌市场中也能盈利（策略保持市场中立）。

### 1.1 **运作机制与特性**

* **1倍名义风险敞口**——全额抵押，零杠杆
* **采用流通市值调整的日度再平衡**
* **全自动算法运行（无需手动调仓）**

### 1.2 BTC **主导金库资金流向**

{% @mermaid/diagram content="flowchart TD
    A[User deposits USDC] --> B(BTC Dominance Vault)
    B --> C(Long BTC)
    B --> D(Short Alt Basket)
    C & D --> E{Daily<br>Rebalance}
    E --> F[Vault P&L]" %}

### 1.3 **实时资产配置（示例为最新快照）**

| 资产       | 实时资产配置（示例为最新快照） | % of Vault AUM |
| -------- | --------------- | -------------- |
| **BTC**  | 做多              | 51%            |
| ETH      | 做空              | 19.9%          |
| XRP      | 做空              | 8.8%           |
| BNB      | 做空              | 6.1%           |
| SOL      | 做空              | 5.2%           |
| 其余前20大资产 | 做空              | 8.0%           |

### 1.4 权重分布可视化（最新快照）

{% @mermaid/diagram content="pie title BTC Dominance Vault – Weights
    "BTC Long" : 51
    "ETH Short" : 19.9
    "XRP Short" : 8.8
    "BNB Short" : 6.1
    "Other Alts Short" : 14.2" %}

***

## **该策略盈利逻辑**

加密货币市场并非单纯上涨或下跌——更存在**轮动效应**。

\
时而比特币领涨，时而山寨币爆发。这种交替走势创造了市场中最稳定的规律之一——而主导金库正是为捕捉此规律而生。

### **您的收益来源：**:

#### 1. **捕捉资金轮动收益**

市场常在“风险偏好”（资金聚焦山寨币）与“风险规避”（资金回归比特币）两种模式间轮动，形成对立两面。

\
只要其中一方表现优于另一方，即便整体价格横盘，您也能获利。

<figure><img src="../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>

#### 2. **风险可控的投资配置**

本策略金库将您的头寸分散投资于经严格筛选的多元化资产组合——涵盖主流公链、DeFi 项目、Meme 币与核心大市值代币，有效降低单一资产暴跌或表现不佳对整体组合的影响。

### **策略速览**:

* **BTC 主导金库** → 做多 BTC / 做空山寨币 → 在 BTC 领涨或回调期间表现更佳
* **山寨币主导金库** → 做多山寨币 / 做空 BTC → 在山寨币季节中表现更优
* 完全市场中立，每日自动再平衡与优化
* 操作简单便捷

***

## **费用与赎回规则**

**绩效佣金**：从本策略为您实现的收益中抽取 **10%**

***

## 存入链接:

Neutral Trade 官网:

{% hint style="info" %}
[https://www.app.neutral.trade/strategies/](https://www.app.neutral.trade/strategies/hyperjlp)
{% endhint %}

Hyperliquid 直达链接:

> BTC Dominance Vault: [https://app.hyperliquid.xyz/vaults/0x799e0112977c37f8d93a768cf5a2305bdd3ae6f9](https://app.hyperliquid.xyz/vaults/0x799e0112977c37f8d93a768cf5a2305bdd3ae6f9)

## 交易查询入口 (Hyperliquid)

{% hint style="info" %}
BTC Dominance Vault: [https://app.hyperliquid.xyz/vaults/0x799e0112977c37f8d93a768cf5a2305bdd3ae6f9](https://app.hyperliquid.xyz/vaults/0x799e0112977c37f8d93a768cf5a2305bdd3ae6f9)
{% endhint %}

***

### Launch date - 25th June 25'
