# Cookie 政策

**最后更新：** 2026-07-25

本 Cookie 政策说明 Neutral Trade（“**我们**”）如何在 **https://www.neutral.trade** 网站、任何相关移动应用程序，以及 Neutral Trade 运营的任何相关界面（统称“**交互界面**”）上使用 Cookie、浏览器本地存储及类似技术。

本政策是对我们[隐私政策](yin-si-zheng-ce.md)的补充，后者更全面地说明了我们如何处理个人数据。隐私政策第 5 节概述了我们对 Cookie 的使用，本政策则提供详细说明。若本政策与隐私政策存在冲突，**以隐私政策为准**。

如对本政策有任何疑问，请联系 **privacy@neutral.trade**。

### 1. Cookie 及类似技术是什么

Cookie 是网站放置在您设备上的小型文本文件。我们同时使用**浏览器本地存储**，其用途相似，但数据保存在浏览器中，而不会随每次请求发送。在本政策中，除非另有说明，提到“Cookie”时均包含本地存储及类似技术。

我们将这些技术分为两类：

* **严格必需** — 用于运行交互界面、实施地区限制、记住您的偏好，以及记录您已做出的选择（包括您对 Cookie 本身的选择）。这类技术无需同意即可启用，因为缺少它们交互界面无法正常运行。
* **分析类** — 用于了解交互界面的使用情况，以便我们改进产品。这类技术是**可选的**。我们会在启用前征求您的同意，您也可以拒绝。

我们不将 Cookie 用于广告，也不为跨场景行为广告共享 Cookie 数据。

### 2. 第一方 Cookie

| 名称               | 类别   | 用途                             | 保留期           |
| ---------------- | ---- | ------------------------------ | ------------- |
| `NEXT_LOCALE`    | 严格必需 | 保存您选择的界面语言                     | 最长 12 个月      |
| `nt_geo_country` | 严格必需 | 保存根据您的连接推导出的粗略国家/地区代码，用于实施地区限制 | 会话期；每次页面请求时刷新 |
| `nt_geo_blocked` | 严格必需 | 保存您的会话是否适用地区限制（`0` / `1`）      | 会话期；每次页面请求时刷新 |

这些 Cookie 以 `path=/` 与 `SameSite=Lax` 设置，并在生产环境中启用 `Secure` 属性。

### 3. 浏览器本地存储

| 键名                               | 类别   | 用途                                       |
| -------------------------------- | ---- | ---------------------------------------- |
| `nt_cookie_consent`              | 严格必需 | 记录您对 Cookie 的选择，以免重复询问                   |
| `neutral-trade-acknowledgements` | 严格必需 | 记录您已确认必要的提示及其时间戳                         |
| `neutral-trade-geo-block`        | 严格必需 | 保存交互界面使用的地区限制状态                          |
| `referral-store`                 | 严格必需 | 保存您通过链接带入的推荐或邀请码及其有效期信息                  |
| `neutral-trade-bookmarks-v2`     | 严格必需 | 保存您在交互界面中收藏的策略                           |
| `theme`                          | 严格必需 | 保存您的浅色、深色或跟随系统的显示偏好                      |
| `nt_api_key_v1`                  | 严格必需 | **仅**在我们的 API 文档页面设置；保存您为测试请求而输入的 API 密钥 |
| `ph_*`                           | 分析类  | 分析标识符与状态，**仅**在您同意分析时写入（见 §4）            |
| `__ph_opt_in_out_*`              | 严格必需 | 若您拒绝分析，仅保存一个记录分析已禁用的标记                   |

清除本地存储可能会重置您的语言、显示偏好、已确认提示及收藏项。

### 4. 分析

我们使用托管于欧盟的 **PostHog** 衡量交互界面的使用情况——例如页面浏览、功能使用与遇到的错误。分析请求通过我们自有的域名路由至 PostHog 的欧盟基础设施。

分析基于同意，具体行为如下：

* **在您做出选择前** — 分析在不使用 Cookie 或持久标识符的情况下运行。浏览器中不保存任何内容，也没有标识符跨访问跟随您。
* **若您接受** — PostHog 会在 Cookie 与本地存储中保存一个标识符（上表中的 `ph_*` 键），以便我们了解跨访问的使用情况。
* **若您拒绝** — 分析采集将在您的浏览器中关闭，不会写入任何分析标识符。唯一保存的是使分析保持禁用状态的标记。

更多信息请参阅 PostHog 的隐私政策：[https://posthog.com/privacy](https://posthog.com/privacy)。

### 5. 第三方服务

交互界面的部分功能由第三方提供，它们可能根据自身政策设置各自的 Cookie 或存储。其对您数据的使用受这些政策约束，而非本政策。

#### 5.1 钱包连接

交互界面集成了 **Reown**（WalletConnect 生态），用于钱包连接、可选的邮箱与社交登录、兑换以及法币入金功能。

* 隐私政策：[https://reown.com/privacy-policy](https://reown.com/privacy-policy)
* Cookie 政策：[https://reown.com/cookie-policy](https://reown.com/cookie-policy)
* 服务条款：[https://reown.com/terms-of-service](https://reown.com/terms-of-service)

#### 5.2 身份提供方

当您选择使用第三方账户登录时，相关认证数据由该提供方按其自身政策处理：

| 提供方        | 隐私政策                                                                                                                                                           |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Google     | [https://policies.google.com/privacy](https://policies.google.com/privacy)                                                                                     |
| X（Twitter） | [https://x.com/privacy](https://x.com/privacy)                                                                                                                 |
| Discord    | [https://discord.com/privacy](https://discord.com/privacy)                                                                                                     |
| GitHub     | [https://docs.github.com/site-policy/privacy-policies/github-privacy-statement](https://docs.github.com/site-policy/privacy-policies/github-privacy-statement) |

#### 5.3 托管

交互界面托管于 **Vercel**，其会处理 IP 地址等技术数据以提供交互界面服务，并提供 §2 中所述的粗略国家/地区信号。

* 隐私政策：[https://vercel.com/legal/privacy-policy](https://vercel.com/legal/privacy-policy)
* 数据处理附加条款：[https://vercel.com/legal/dpa](https://vercel.com/legal/dpa)

### 6. 您的选择

* 首次访问交互界面时，您可通过提示**接受**或**拒绝**分析。严格必需的技术不受此选择影响。
* 若要更改已做出的选择，请在浏览器设置中清除本站数据。提示将在您下次访问时再次出现。
* 您可随时通过浏览器设置阻止或删除 Cookie。
* 若处理基于同意，您可随时撤回同意，而不影响撤回前已进行处理的合法性，具体见隐私政策 §6。

阻止或清除**严格必需**的 Cookie 与本地存储，可能影响交互界面的正常运行，包括语言选择、地区限制逻辑与钱包连接。

### 7. 本政策的变更

若我们对 Cookie 的使用发生变化，我们将更新本政策并修订上方日期。若变更具有重大影响，我们将采取合理方式通知您，例如在交互界面上发布提示。

### 8. 联系我们

如对本 Cookie 政策有任何疑问，请联系 **privacy@neutral.trade**。
