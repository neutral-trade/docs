---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/6YjCIQB3ardoMeqGMIF8/for-capital-allocators/usdc-yield/market-neutral/hyperliquid-funding-arb
---

# Hyperliquid 资金费率套利策略

## 概览

Hyperliquid 资金费率套利金库通过捕获 Hyperliquid 永续合约市场中的资金费率失衡来获取收益。策略同时持有相互对冲的现货与永续合约仓位，以保持 Delta 中性。收益来自永续合约市场参与者对杠杆的结构性需求。

另有 10% 的仓位配置于 Hyperliquidity Provider（HLP）金库，用以分散收益来源，并在极端看跌波动期间提供额外的收益稳定性。

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>存入</strong></td><td><a href="https://www.neutral.trade/strategies/hlfundingarb">https://www.neutral.trade/strategies/hlfundingarb</a></td></tr></tbody></table>

_自 2025 年 6 月 11 日起上线_

## 运作方式

金库对同一资产同时建立现货多头与永续合约空头仓位，目标是净方向性敞口为零。当资金费率为正时（即市场净多头，这是绝大多数市况下的结构性状态），资金费会从永续合约空头仓位流向金库。

**示例：**

* 现货做多 1 HYPE → delta = +1
* 永续合约做空 1 HYPE → delta = −1
* **净 delta = 0**
* 永续合约空头仓位的资金费收入归属金库

随着价格变动与资产组合变化，系统会自动再平衡仓位以维持 Delta 中性。

**HLP 配置：** 10% 的 USDC 储备配置于 Hyperliquid 原生的 HLP 金库，该金库从 Hyperliquid 的做市活动、清算费与平台费中获取收益。

## 收益来源

* **永续合约资金费** — 由使用杠杆的多头参与者支付给空头持有者
* **现货与永续合约的定价错配** — 当现货与永续合约价格偏离时捕获的额外价差
* **HLP 收益** — 做市收入、清算费与平台费

## 风险因素

**资金费率风险** — 费率可能转为负值，此时金库将支付而非收取资金费。当净收益不再足以覆盖成本时，仓位会被调整。

**HLP 风险** — 在严重的市场定价偏离中，HLP 可能因做市敞口而产生亏损。10% 的配置上限限制了其对金库整体表现的影响。

**清算风险** — 金库以低杠杆运作。保证金健康度受到持续监控，并在接近清算阈值前自动再平衡。

**智能合约风险**

## 托管与安全

金库资产在 Neutral Strategy Vaults 标准的封闭环境框架下运行：所有资金转移均需多方审批，仅允许白名单提款地址，且任何单一密钥持有人都无法单方面授权交易。详见：[《安全机制》](../../zhong-xing-ce-le-jin-ku/an-quan-ji-zhi.md)。
