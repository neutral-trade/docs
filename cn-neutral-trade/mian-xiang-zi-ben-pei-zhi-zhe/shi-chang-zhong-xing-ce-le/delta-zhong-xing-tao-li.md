---
hidden: true
---

# Delta 中性套利

## 概览

Delta 中性套利是由 Velox Trading Group 管理的市场中性套利策略金库。该策略致力于在降低加密市场整体下行风险的同时，最大化绝对收益。为实现这一目标，策略将资金部署到四大套利支柱上：低延迟交易所套利、资金费率与基差套利，以及以 DeFi 为中心的做市。

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>存入</strong></td><td><a href="https://www.neutral.trade/strategies/velox-cross-usdc-bundle">https://www.neutral.trade/strategies/velox-cross-usdc-bundle</a></td></tr></tbody></table>

_在 Neutral Trade 上线时间：2026-06-09_

_过往业绩不代表未来表现。_

## 运作方式

策略同时运行四个互补的套利支柱。

* **低延迟交易所套利**
* **资金费率与基差套利**
* **以 DeFi 为中心的做市**

除交易所与衍生品杠杆之外，组合目标现金杠杆率为 1.5 倍。这是一项长期目标，借助主经纪商提供的杠杆来提升整体收益特征。

#### 交易场所

**中心化交易所：** Binance、OKX、Bybit、Gate

**去中心化交易所：** Hyperliquid、Lighter

后续阶段将新增：

* KuCoin

### 收益来源

* 通过同步对冲交易捕获的跨场所定价无效性
* 通过 Delta 中性建仓捕获的资金费率与基差
* 市场事件前后的短期定价偏离

## 风险因素

**交易对手与交易所风险** — 跨交易所交易会产生场所层面的失败、破产或运营中断风险。缓解措施包括：对中心化交易所交易采用 Copper（ClearLoop）与 Ceffu（MirrorX）提供场外托管与结算，以及上线时即分散于六个交易场所（后续还将新增）。

**清算与自动减仓风险** — 策略以 1.5 倍杠杆运作。剧烈价格波动或多场所同时承压，可能触发永续合约仓位的强制清算或自动减仓。缓解措施包括：相对典型套利策略更保守的杠杆水平、持续的仓位监控，以及仅在再平衡可靠的高流动性市场交易。

**执行与市场微观结构风险** — 做市与短周期策略对执行质量高度敏感。逆向选择（在方向性行情中被成交在错误一方）会侵蚀价差收入。

**智能合约风险** — 以 DeFi 为中心的做市需与链上协议交互，因此会继承这些场所的智能合约风险。该风险无法完全消除。

**运营风险** — 跨多个交易场所、多个策略的执行依赖于交易基础设施、交易所 API 与托管集成服务的持续可用性。任一环节中断都可能导致无法及时完成再平衡。

## 托管与安全

对于中心化交易所上的仓位，我们使用机构级场外结算服务商 Copper（ClearLoop）与 Ceffu（MirrorX），以降低交易所层面的破产风险。

链上金库基础设施（涵盖存入、提取与链上操作）在 Neutral Strategy Vaults 标准的多方审批框架下运行，独立于中心化交易所的托管安排。详见：[《安全机制》](../../zhong-xing-ce-le-jin-ku/an-quan-ji-zhi.md)。

## 为什么选择 Velox Trading Group？

[Velox Trading Group](https://www.veloxtrading.ai/) 是一家数字资产量化投资与技术公司。团队由交易员、工程师、数学家与数据科学家组成，专精中心化与去中心化场所的加密市场微观结构。
