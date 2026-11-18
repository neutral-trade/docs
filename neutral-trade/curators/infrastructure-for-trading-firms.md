---
description: You keep the strategy. We run everything else.
---

# Infrastructure for Trading Firms

A profitable strategy is not enough to manage outside capital. You also need an account on every venue, a custodian behind each exchange, an MPC wallet for on-chain venues, a way to move collateral between them, a daily NAV, fee accounting for each investor, and reporting. Most trading firms rebuild that stack for every investor, as one more managed account.

Neutral Trade has built it once, as shared infrastructure. You connect your strategy to a [Neutral Strategy Vault](../neutral-strategy-vaults/how-they-work.md) and trade. We operate the rest.

## What You Keep and What We Run

| You keep                        | Neutral Trade runs                                  |
| ------------------------------- | --------------------------------------------------- |
| Your strategy, code and signals | Vault smart contracts and on-chain share accounting |
| Execution and risk decisions    | Custodian and MPC integrations across 9 venues      |
| Your track record               | Collateral transfers between venues                 |
|                                 | Daily NAV and share pricing                         |
|                                 | Deposits, redemptions and fee settlement            |
|                                 | Reporting, monitoring and depositor support         |

Your strategy IP stays with you. There is no code disclosure, no replication commitment, no exclusivity and no non-compete.

## 9 Venues, Already Integrated

| Venue            | Type                 | Custody and signing |
| ---------------- | -------------------- | ------------------- |
| Binance          | Centralized exchange | Ceffu (MirrorX)     |
| KuCoin           | Centralized exchange | Ceffu (MirrorX)     |
| OKX              | Centralized exchange | Copper (ClearLoop)  |
| Bybit            | Centralized exchange | Copper (ClearLoop)  |
| Gate             | Centralized exchange | Copper (ClearLoop)  |
| Bitget           | Centralized exchange | Copper (ClearLoop)  |
| Hyperliquid      | Perpetual DEX        | Fordefi MPC         |
| Lighter          | Perpetual DEX        | Fordefi MPC         |
| TradFi brokerage | Brokerage            | Brokerage account   |

Neutral Trade is integrated with two institutional custodians and one MPC provider. You do not open, fund or maintain any of those relationships.

* **Centralized exchanges.** Capital stays in off-exchange custody with Ceffu or Copper and is mirrored to a dedicated sub-account. You trade at your fee tier or ours: in your own sub-account (MSA, managed sub-account), or in a sub managed account (SMA) that Neutral Trade provides.
* **Perpetual DEXs.** Accounts are held under Fordefi MPC policies. You trade with a trading key that Neutral Trade issues.

Other venues are scoped per strategy after a technical call. The custody model is described in full on [Security](../neutral-strategy-vaults/security.md).

## Move Collateral in One Request

Cross-venue strategies need collateral in the right place at the right time. The Transfer API takes one request: source venue, destination venue, amount and currency. Neutral Trade routes the transfer in USDC through whitelisted MPC receivers and Circle's Cross-Chain Transfer Protocol (CCTP), then confirms completion.

You do not withdraw from one exchange and deposit to another by hand, and there is no address to mistype.

## Accounting and Billing, Automated

* **Daily NAV.** We read live account equity from read-only API keys on every venue, mark collateral to USDC at the live rate, and publish the price to the vault's on-chain oracle each day. Shares are minted and redeemed at that NAV.
* **One account, many investors.** You manage a single account. The vault tracks every depositor's shares on-chain.
* **High-water-mark fees.** Performance fees are calculated per wallet against an individual high-water mark and settled automatically. You send no invoices and carry no collection risk. Neutral Trade takes a share of the performance fee, as set in your agreement, and collects a 1% management fee from depositors for custody and operations.
* **Month-end statements.** You receive a fee and distribution statement at each month end.

This replaces a fund administrator's NAV calculation and the monthly reconciliation between your books, the custodian and the exchange.

## Your One Recurring Task

On a centralized exchange, deposits arrive as USDC in the venue's Spot account. Move them to your trading account to trade.

Before each withdrawal batch, the reporting bot tells you how much USDC to have in Spot. Move that amount from your trading account to Spot, by hand or through the exchange API. Neutral Trade does the rest: it withdraws from Spot, settles on-chain and pays each depositor. Neutral Trade never withdraws from open positions.

Other venues follow the same pattern, with the account agreed at onboarding. Processing times and the withdrawal schedule are set in your vault terms, and the operator guide you receive at onboarding gives the exact steps.

## Reporting

A dedicated Telegram reporting bot for your vault sends:

* Daily deposit and withdrawal acknowledgments
* A notice before each withdrawal batch, with the amount to have in Spot
* A weekly fund-flow report: unlocked withdrawals, pending withdrawals and net flow
* A month-end fee and distribution statement

Your operations desk and your investors work from the same daily facts.

## A Structure Depositors Can Verify

You receive execution permissions only. Vault capital cannot be withdrawn to an arbitrary external address, by you or by Neutral Trade. Every movement is restricted to pre-approved addresses, contracts and custody routes.

That protects depositors. It also helps you raise capital: an allocator does not have to take your word on custody before depositing. See [Vault Protections](../neutral-strategy-vaults/vault-protections.md) and [Security](../neutral-strategy-vaults/security.md).

## Get the Most from Neutral Trade

You bring the strategy. The firms that do best on Neutral Trade also use the platform around it. These nine habits protect your net return, keep your operations quiet, and help your vault raise capital.

1. **Trade at the best fee tier.** Your tier or ours. If your VIP tier or rebates beat ours, trade in your own sub-account and confirm the tier is active before launch. Most differences between your own books and the vault return come from a fee-tier gap.
2. **Set vault terms that fit your desk.** Before launch we agree the deposit schedule, redemption notice, any deposit lock and a capacity cap with you. Set them around your desk's coverage hours and how quickly you can unwind. Fewer forced unwinds, steadier performance.
3. **Let us move your collateral.** One request per transfer between venues. No manual withdrawals and deposits, and no address to mistype.
4. **Run daily controls from one feed.** Deposits, withdrawals, daily equity, a weekly fund-flow summary and fee notices arrive in your ops group. Your desk and your depositors work from the same numbers.
5. **Let fees collect themselves.** Performance fees per depositor against individual high-water marks, collected and paid to you monthly. No invoices, no collection risk.
6. **Build a track record allocators can check.** On-chain NAV and trading permissions only: firms can trade, they cannot withdraw. Allocators verify your record and your custody themselves, so due diligence goes faster.
7. **Talk to your depositors.** A short monthly commentary on your vault page — what happened, what you changed, what you expect — keeps depositors in. Context, not positions. You can launch under an alias.
8. **Grow in stages.** Your vault goes live on Neutral Marketplace about 3–4 weeks after terms are agreed. After 3+ months of good performance it moves to Neutral Curated. You can also run a private vault for your own investors on the same infrastructure, and partners with a live vault get priority for a second strategy.
9. **Offer VIP tiers to win bigger tickets.** Set Silver, Gold and Diamond tiers by a depositor's balance in your vault, with a performance-fee discount at each tier. Depositors claim their tier in the app, and the discount is applied to their wallet on-chain. It attracts larger depositors without changing your headline fee.

## Two Ways to Launch

|                | Listed vault                                                                   | Private vault      |
| -------------- | ------------------------------------------------------------------------------ | ------------------ |
| Who deposits   | Neutral Trade depositors and distribution partners                             | Your own investors |
| Listing        | Neutral Marketplace first; Neutral Curated after 3+ months of good performance | Not listed         |
| Infrastructure | Custody routes, NAV, redemptions and reporting                                 | The same           |

Listed strategies are assessed under [Curator Selection](curator-selection.md).

## Get Started

Fill in the [application form](https://forms.gle/wKKsqBZmwLkZW4gk8), message the team on [Telegram](https://t.me/neutraltrade), or email [partnerships@neutral.trade](mailto:partnerships@neutral.trade). [Curator Onboarding](curator-onboarding.md) sets out the steps and the timeline.
