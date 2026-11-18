# JLP Delta 中性增强策略

## **概览**

JLP Delta 中性增强金库通过参与 Jupiter 的 JLP 流动性提供获取收益，同时系统性地对冲所有针对 SOL、BTC 和 ETH 的方向性敞口。

策略持续将净 Delta（Net Delta）维持在接近零的水平，收益主要来自 JLP 交易手续费和借贷费用（Borrowing Fees），而非资产价格上涨或下跌带来的方向性收益。

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>DEPOSIT</strong></td><td><a href="https://www.neutral.trade/strategies/jlpdn">https://www.neutral.trade/strategies/jlpdn</a></td></tr></tbody></table>

## **运作机制**

### 利用 JLP 提升收益

JLP 是 Jupiter 的流动性提供者代币，可获得 Jupiter Perps 平台全部费用收入的 75%，包括：开仓费用、平仓费用、价格影响费用、交易手续费、借贷费用。

该金库通过循环杠杆机制（Looping Process）放大这部分收益：

1. 将存入的 USDC 通过 Jupiter Perps 机制铸造 JLP；
2. 将 JLP 存入 [Jupiter JLP Loans ](https://jup.ag/perps/jlp-loans)作为抵押品
3. 以该抵押品借出 USDC；再将借出的 USDC 用于购买更多 JLP。

<figure><img src="../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

### **Delta 中性对冲**

由于其代币构成以及交易者盈亏（PnL）的影响，JLP 持有 SOL、BTC 和 ETH 的风险敞口。自动化对冲引擎通过以下方式将这些敞口中和：

1. 将借出的 USDC 转入 Ceffu 托管体系，并镜像至由 Jupiter 与 Neutral Trade 共同管理的 Binance 子账户；
2. 持续监控 JLP 的方向性风险敞口；
3. 在 Binance 开立永续合约空头仓位，以抵消相关敞口；
4. 根据 JLP 的资产构成和市场状况，动态调整对冲权重。

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

## 收益来源

* **JLP 原生收益** —— 来自 Jupiter Perps 平台全部费用收入的 75%。
* **杠杆放大收益** —— 循环杠杆结构相较于未加杠杆的持仓，可提高有效收益率。
* **资金费率收益** —— 对冲仓位产生的资金费率在特定市场环境下可能带来额外收益，但也可能构成成本。

## 风险因素

**JLP 代币风险** —— 在市场快速波动期间，JLP 的市场价格可能相对于其虚拟价格出现偏离。此外，对冲仓位的再平衡会产生交易成本，因此存在一个成本阈值，在该阈值以下策略不会维持完全的 Delta 中性状态。

**Exchange and settlement risk交易所与结算风险** —— 对冲仓位持有于 Binance。因此仍面临流动性风险、市场错位风险以及自动减仓风险。中心化交易所托管风险通过 Ceffu 提供的场外托管与结算服务进行缓释。抵押资产并不存放于 Binance 的资产负债表上。

**运营风险** —— 链下 Delta 计算以及 Ceffu 与链上金库之间的每日盈亏（PnL）结算属于策略运行中的关键运营依赖环节。这些流程均按照 Neutral 策略金库的多方审批框架进行管理。

**智能合约风险**

## 托管与安全

该金库采用 Neutral 策略金库标准的封闭式管理框架运行。所有资金划转均需经过多方审批；仅允许向白名单地址进行资金操作；不存在任何单一密钥持有人能够单独执行资金操作。抵押资产由 Ceffu MPC（多方计算）托管体系保管，不存放于交易所资产负债表内。

金库基础设施已通过 Quantstamp、Halborn 和 Offside Labs 的审计。完整详情请参阅：[**安全机制**。](https://docs.neutral.trade/vault-infrastructure/security)
