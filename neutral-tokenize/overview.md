---
description: >-
  Neutral Tokenize turns a Neutral Strategy Vault position into a token you hold
  in your own wallet. Coming soon, starting with Neutral Autopilot.
---

# Overview

Hedge fund strategies, held as a token in your wallet.

{% hint style="warning" %}
**Coming soon.** Neutral Tokenize is not live. No launch date is announced, and the details on this page can change before launch. Follow [Neutral Trade on X](https://x.com/TradeNeutral) for the announcement.
{% endhint %}

## What Is Neutral Tokenize?

Neutral Tokenize is a new way to hold a [Neutral Strategy Vault](../neutral-strategy-vaults/how-they-work.md). You deposit USDC and receive a token that represents your share of the vault. The token sits in your own wallet, and its value follows the vault's share price.

The first tokenized vault is planned to be [Neutral Autopilot](../for-capital-allocators/neutral-autopilot.md), the multi-strategy vault that allocates across Neutral Trade's live strategies.

Our goal is to open hedge fund grade strategies to everyone. A vault removed the $1M minimum, the paperwork, and the quarterly lock-up. A token removes the last step: you do not need to learn a new app to hold a professional strategy. You hold one token, the same way you hold any other asset on Solana.

## How It Works

1. **Mint.** You deposit USDC on Neutral Trade. The vault program issues tokens to your wallet in the same transaction, at the vault's current share price. You set a minimum amount of tokens to receive, so the transaction fails if the price moves against you.
2. **Hold.** The strategies keep trading. You do not receive separate yield payments. Gains and losses are reflected in the price of the token, which follows the vault's net asset value (NAV) after fees.
3. **Redeem.** You return tokens to Neutral Trade to request a withdrawal. The request follows the vault's normal redemption schedule, and USDC is paid to your wallet at settlement.

The vault manager can set a cap on how much can be minted in each processing cycle. When the cap is reached, a mint transaction fails and you can try again in the next cycle.

## What You Can Use the Token For

| Use                                                                                 | Status    |
| ----------------------------------------------------------------------------------- | --------- |
| Hold a professional strategy in any Solana wallet, next to your other assets        | At launch |
| Transfer your position to another wallet, for example to cold storage or a multisig | At launch |
| Mint in one transaction, subject to the per-cycle cap                               | At launch |
| Find the token in wallets and aggregators                                           | Planned   |
| Use the token as collateral on Solana lending markets                               | Planned   |

Planned integrations depend on third-party protocols. Each one is announced when it is live. This page does not promise a date for any of them.

## Token or Vault Deposit?

Neutral Tokenize does not replace vault deposits. Both stay available in the Neutral Trade app.

| Topic                  | Neutral Tokenize                                            | Vault deposit                                |
| ---------------------- | ----------------------------------------------------------- | -------------------------------------------- |
| **Built for**          | Users who want to hold one asset                            | Allocators who select and monitor strategies |
| **What you hold**      | A token in your wallet                                      | A vault position recorded for your wallet    |
| **Choice of strategy** | Tokenized vaults, starting with Neutral Autopilot           | All listed strategy vaults                   |
| **Transferable**       | Yes, as a standard Solana token                             | No                                           |
| **High-water mark**    | One for the token pool                                      | One for each wallet                          |
| **Analytics**          | Token price and yield                                       | Full performance, risk, and allocation data  |
| **Exit**               | Redeem on Neutral Trade, on the vault's redemption schedule | Withdraw on the vault's redemption schedule  |

To redeem, the holder needs a Neutral Trade account for that vault and must meet the same regional restrictions as a depositor.

## Fees

The token price is net of the vault's fees. The vault program charges the management fee and any performance fee to the tokenized pool as a whole, so every token carries the same price.

{% hint style="info" %}
**The high-water mark works differently for a token.** For a tokenized vault, the high-water mark is tracked for the token pool, not for your wallet. A performance fee on the pool's profit is reflected in the token price for every holder. If the pool is below its high-water mark when you mint, you can gain from the recovery without a performance fee on that part. A direct vault position has its own high-water mark for each wallet.
{% endhint %}

An issuance fee is charged in tokens when you mint, in addition to the vault's deposit fee if one is set. The fee schedule for each tokenized vault will be published on this page and in the app before launch. See [Fees + Redemption Period](../additional-info/fees-+-redemption-period.md) for how vault fees work today.

## Security

The token is issued by the same audited Solana program that runs every Neutral Strategy Vault.

* The token's mint authority is a program-derived address, not a team wallet.
* The program mints tokens only in the deposit instruction and burns them only in the redemption instruction.
* The vault manager can set the issuance fee and the per-cycle mint cap.

The most recent audit, by Adevar Labs in October 2026, reviewed the vault program including its tokenized shares. The report lists recommendations to complete before a vault is tokenized. All four audit reports are on the [Security](../neutral-strategy-vaults/security.md) page.

## Risks

A token is a different way to hold a vault. It is not a lower level of risk.

* **Strategy risk.** The token price follows the vault. If the strategies lose money, the token price falls. See the [Risk Overview](../for-capital-allocators/risk-overview/).
* **Redemption timing.** The exit is a redemption on Neutral Trade, on the vault's schedule. You stay exposed to the token price until settlement.
* **No guaranteed market price.** If the token trades on a third-party venue, that price can differ from the vault's NAV. Neutral Trade does not guarantee liquidity on any third-party venue.
* **Third-party protocol risk.** If you use the token as collateral, you take on the risks of that protocol, including liquidation.
* **Smart contract risk.** Audits reduce this risk. They do not remove it.
* **Wallet risk.** The token is a bearer asset. If you send it to a wrong address or lose access to your wallet, Neutral Trade cannot recover it.

## Common Questions

**Is Neutral Tokenize live?**

No. It is in development and no launch date is announced.

**Which vault is tokenized first?**

Neutral Autopilot is planned to be the first. Private vaults are not tokenized.

**Does the token pay yield to my wallet?**

No. The token does not rebase and does not pay out. Gains and losses are reflected in the token's price.

**How do I exit?**

You redeem the token on Neutral Trade. The request follows the vault's redemption schedule, and USDC is paid at settlement.

**Can I still deposit into a vault directly?**

Yes. Vault deposits remain available in the Neutral Trade app.

**Is the token available in every country?**

No. The same restrictions apply as for the vaults. See [Regional Availability](../legal/regional-availability.md).

_Products referenced are not intended for individuals in the United States, Mainland China, Hong Kong, sanctioned, or other restricted jurisdictions. This page is for informational purposes only and does not constitute an offer, solicitation, or recommendation to buy or sell any financial instrument. Digital-asset strategies involve significant risk, including possible loss of principal. See the_ [_Risk Warnings and Disclaimers Statement_](../legal/risk-warnings-and-disclaimers-statement.md)_._
