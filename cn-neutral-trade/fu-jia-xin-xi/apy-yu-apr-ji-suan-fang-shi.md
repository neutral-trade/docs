---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/6YjCIQB3ardoMeqGMIF8/additional-info/apy-and-apr-calculations
---

# APY 与 APR 计算方式

APR 的计算基于当前 PPS（每份额价格，Price Per Share）与此前某一时间点 PPS 的对比。通常采用过去 90 天的数据进行计算，但具体周期可能会根据金库（Vault）的存续时间及其他因素有所调整。

关于 APR，以及毛 APY（Gross APY）和净 APY（Net APY）的具体信息，您可以在应用中任意金库页面，将鼠标悬停在 APY 图标上进行查看。

APR 反映的是历史业绩表现，并不构成任何收益保证，但它能够清晰展示在相应统计期间内存款人实际获得的收益水平。

请注意，APR 为费用扣除前（Gross）的收益率数据，尚未计入相关费用。

**`APR = 收益率 * (365 / 统计周期天数)`** \
**`统计周期天数 = 过去 90 天`**\
&#x20;**`收益率= (期末价值 - 期初价值) / 期初价值`**

对于 APY 数值，我们采用**按日复利公式**进行计算：

```
APY=(1+APR/365)*365−1
```
