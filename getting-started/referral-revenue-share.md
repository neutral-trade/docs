# Referral Revenue Share

Your Neutral Trade referral link has always earned NT Points. Since 4 September 2026 the same link can also pay you a share of the management fee on every deposit that comes through it. This page shows how to turn it on and how the payout works.

Revenue share uses the same ladder and the same on-chain mechanism as the [Builders Code Rebate](../for-distribution-partners/neutral-builders-code.md). The difference is the entry point: you turn it on from the referrals page with one signature, and you do not need to integrate anything.

## Turn it on in three steps

### Step 1. Get your referral code

1. Go to [neutral.trade/referrals](https://www.neutral.trade/referrals) and connect your wallet.
2. If you do not have a code yet, press **Generate my code**. This is one wallet signature, not a transaction.
3. Your code appears under **Your referral code**, for example `YR92AC`. **Copy Link** gives you the full link in the form `https://www.neutral.trade/strategies?r=YR92AC`.

A link that exists but has not been opened for revenue share earns NT Points only. The **Revenue share** card on the same page tells you which state you are in.

### Step 2. Enable revenue share

1. Scroll to the **Revenue share** card. While it reads **NOT OPENED**, your link earns points only.
2. Press **Enable revenue share**. This opens the registration dialog at [neutral.trade/builder/register](https://www.neutral.trade/builder/register).
3. Every vault with revenue share switched on is pre-ticked. Each row shows the vault's **1% management fee**.
4. Read the terms in the dialog, then press **Confirm and sign**. One signature registers you on all selected vaults.

After the transaction confirms, the card reads **Revenue share is on** with a counter such as **10 / 10 vaults**. If the counter is below the total, the card offers to open the remaining vaults.

### Step 3. Share your link

Share the link from **Share Referral Link** or paste it anywhere. When someone opens it and deposits into a vault, the code rides along with the deposit. There is nothing for them to submit.

Attribution is set on the person's **first deposit into that vault** and cannot be added later. If someone already holds a position in a vault before they use your link, you earn points on them but not a fee share in that vault. Turn revenue share on before you start sharing.

## What you earn

You receive a share of the **1% annual management fee** that the vault charges the users you referred. Performance fees are not shared.

| Referred net deposits in a vault | Your share of the management fee |
| -------------------------------- | -------------------------------- |
| Below $10,000                    | 0%                               |
| $10,000 to below $500,000        | 10%                              |
| $500,000 to below $3,000,000     | 20%                              |
| $3,000,000 to below $5,000,000   | 30%                              |
| $5,000,000 to below $10,000,000  | 40%                              |
| $10,000,000 and above            | 50%                              |

Thresholds are inclusive at the lower bound. Referred net deposits are the deposits your referred users made into that vault minus their withdrawals from it, not the market value of their positions.

**Worked example.** Your referred users hold $600,000 of net deposits in one vault. You are in the 20% tier for that vault. If that capital pays the full 1% management fee for a year, the fee is $6,000 and your share is $1,200. The fee accrues over time, so this is an annualised illustration, not a fixed payment.

On top of the fee share, you keep earning **10% of the NT Points** your referred users earn, as before.

## Rules to know

* **Your cut comes out of the manager's fee.** Referred users pay nothing extra.
* **The ladder is counted per vault.** $400,000 in each of two vaults is 10% in each vault, not 20% on $800,000.
* **Your tier is live.** It follows what your referred users hold in that vault right now, so it can move down as well as up. Existing referred users move with you.
* **VIP discounts come first.** Your share is taken from the fee the user actually pays, after any [Neutral VIP Program](neutral-vip-program.md) discount they hold. A user on a 20% discount pays 0.8%, and your tier percentage applies to that amount.
* **Earnings accrue as vault shares.** Their value moves with the vault's price per share. Claiming goes through the vault's redemption cycle, so payout is not instant.
* **One wallet.** The wallet you sign with becomes your Builder ID and is the wallet that receives earnings.

## Track and claim

Your dashboard at [neutral.trade/builder](https://www.neutral.trade/builder) shows, per vault, your referred users, referred net deposits, current tier, and claimable earnings. Press **Claim** to request a payout. A keeper settles the request after the vault's cooldown, and settled claims appear in your claim history.

## Frequently asked questions

**Do I need to deposit to enable revenue share?** Some vaults set a minimum builder deposit for registration. The registration dialog shows **Ready to register** or the amount to deposit for each vault.

**I have been sharing my link for a while. Do past deposits count?** No. Attribution is written into a user's first deposit transaction for a vault. Deposits made before you enabled revenue share earn NT Points only.

**Can I enable revenue share on more vaults later?** Yes. When a vault manager turns revenue share on, the counter on your referrals card drops below the total and the card offers to open the remaining vaults.

**Is this the same as the Builders Code?** Yes. Revenue share is the Builders Code Rebate reached from the referrals page. Partners who integrate the SDK use the same ladder and the same dashboard. See [How Builder Codes Work](../for-distribution-partners/how-builder-codes-work.md) for the on-chain detail.
