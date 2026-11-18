---
icon: alicorn
---

# \[Hyperliquid] ALT Dominance \[Deprecated]

{% hint style="danger" %}
**⚠️ Deprecated vault — historical reference only.**

This vault has been deprecated and is no longer active on Neutral Trade. It is not accepting deposits and is not part of the current product line-up. Do not present this strategy as available or current. For live vaults and current data, see the active strategies and the API reference at https://www.neutral.trade/api/v1/docs.
{% endhint %}

<figure><img src="https://1924233991-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F6YjCIQB3ardoMeqGMIF8%2Fuploads%2FRslr3l7vMDxqJ9grYi0A%2F123.png?alt=media&#x26;token=a737723e-e5a2-42c2-bda4-b482189623dc" alt=""><figcaption></figcaption></figure>

Neutral Trade is now live on Hyperliquid — starting with our [Funding Arb](../usdc-yield/market-neutral/hyperliquid-funding-arb.md) strategy and expanding with two brand-new Dominance Vaults, built directly on Hyperliquid’s native vault infrastructure.

{% hint style="info" %}
Save more on Hyperliquid! Use our Referral Code:

[https://app.hyperliquid.xyz/join/NEUTRALTRADE](https://app.hyperliquid.xyz/join/NEUTRALTRADE)
{% endhint %}

<figure><img src="https://1924233991-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F6YjCIQB3ardoMeqGMIF8%2Fuploads%2F1uMlvgoYTXQlrJsBYB6h%2FDrafts%20for%20posting%20(dont%20delete)%20(38).png?alt=media&#x26;token=295239f6-19cf-4f5b-8502-1a92d56292d4" alt=""><figcaption></figcaption></figure>

## 🤔 What is Dominance?

Dominance shows how much of the total crypto market is allocated to a specific asset — **BTC** or **Altcoins.**

### ➗Formulas:

$$
\text{Dominance}_{BTC} = \frac{\text{Market Cap}_{BTC}}{\sum_{i=1}^{N} \text{Market Cap}_i}
$$

This ratio reflects capital flows:

* **BTC Dominance ↑** → Capital is rotating into Bitcoin (risk-off)
* **BTC Dominance ↓** → Capital is rotating into altcoins (risk-on)

**ALT Dominance** is simply the inverse:

$$
\text{Dominance}_{ALT} = 1 - \text{Dominance}_{BTC}
$$

## 1. ALT Dominance Vault

<figure><img src="https://1924233991-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F6YjCIQB3ardoMeqGMIF8%2Fuploads%2FcmwTQUFqwzYmhtQwEI1O%2Fchrome_yB5yFrxNsl.png?alt=media&#x26;token=d5e8986f-8d63-46e9-a6fb-4fbe7b4908bb" alt=""><figcaption></figcaption></figure>

#### This vault targets **altcoin strength relative to BTC** — also known as ALT SEASON

It goes:

* **Long top-20 altcoins** (ETH, SOL, meme coins, etc.)
* **Short BTC** as the hedge

You earn when altcoins **outperform Bitcoin**, regardless of market direction

### 1.1 Mechanics and features

* Fully collateralized, 1× notional exposure
* Cap-weighted altcoin basket updated daily
* Automated algorithms (No manual rebalancing)
* Market-neutral (You are only exposed to BTC/ALT dominance)

### 1.2 ALT Dominance Vault Flow

```mermaid
flowchart TD
    A[User deposits USDC] --> B(ALT Dominance Vault)
    B --> C(Short BTC)
    B --> D(Long Top Alts Basket)
    C & D --> E{Daily<br>Rebalance}
    E --> F[Vault P&L]
```

### 1.3 Live Allocation (The latest snapshot for example)

| Asset       | Direction | % of Vault AUM     |
| ----------- | --------- | ------------------ |
| Top-20 Alts | Long      | 49% (cap-weighted) |
| BTC         | Short     | 51%                |

### 1.4 Weights Visualization (The latest snapshot)

```mermaid
pie title ALT Dominance Vault – Weights
    "Top 20 Alts Long (ETH, XRP, BNB, SOL..)" : 49
    "BTC Short" : 51
```

***

## How You Make Money

Crypto doesn’t just move up or down — it **ROTATES**

Sometimes Bitcoin leads. Sometimes altcoins run. That back-and-forth creates one of the most reliable patterns in the market — and **Dominance Vaults** are built to capture it

### Here's how you benefit:

#### 1. **Profit from Capital Rotation**

Markets frequently rotate between **risk-on** (focused on altcoins) and **risk-off** (focused on Bitcoin) phases, representing two flip sides.

You make money when one side **outperforms** the other, even if overall prices stay flat.

<figure><img src="https://1924233991-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F6YjCIQB3ardoMeqGMIF8%2Fuploads%2FSKA5phY5fZJR5sOBJ9PX%2Fimage%20(10).png?alt=media&#x26;token=3fa187cf-21b6-4a98-88c6-9a38a3f3f372" alt=""><figcaption></figcaption></figure>

#### 3. Risk-controlled investment

The vaults spread your position across a carefully selected basket of assets — including L1s, DeFi, memes, and majors — to reduce the impact of any single token blowing up or underperforming

### TLDR:

* **BTC Dominance Vault** → Long BTC / Short Alts → Works best during BTC rallies or corrections
* **ALT Dominance Vault** → Long Alts / Short BTC → Works best during altcoin season
* 100% market-neutral, daily-rebalanced and auto-optimized
* Easy to use

***

## Fees & Withdrawals

10% performance fee on profits our trading made for you.

***

## Deposit Links:

Neutral Trade website:

{% hint style="info" %}
[https://www.app.neutral.trade/strategies/](https://www.app.neutral.trade/strategies/hyperjlp)
{% endhint %}

Hyperliquid directly:

> ALT Dominance Vault: [https://app.hyperliquid.xyz/vaults/0xb03715bec4514ae7d338fcd85053ca227a1fb823](https://app.hyperliquid.xyz/vaults/0xb03715bec4514ae7d338fcd85053ca227a1fb823)

## Check Positions Here (Hyperliquid)

{% hint style="info" %}
ALT Dominance Vault: [https://app.hyperliquid.xyz/vaults/0xb03715bec4514ae7d338fcd85053ca227a1fb823](https://app.hyperliquid.xyz/vaults/0xb03715bec4514ae7d338fcd85053ca227a1fb823)
{% endhint %}

***

### Launch date - 25th June 25'
