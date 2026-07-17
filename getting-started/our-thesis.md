---
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Our Thesis

> **"This is a game where normal people lose... because you're competing with professional traders and quants." — Derek, CEO of Neutral Trade**

Crypto markets have a structural asymmetry.&#x20;

On one side: systematic hedge funds running delta-neutral, arbitrage, volatility, and momentum strategies at institutional scale, with the infrastructure, venue access, and operational machinery to compound their edge.&#x20;

On the other side: everyone else, taking directional bets into liquidity those funds provide and adverse selection those funds capture.

Neutral Trade exists to close that gap. We give allocators direct access to these strategies through a vehicle purpose-built for on-chain capital.

***

### The allocator problem

Today, an allocator who wants exposure to professional systematic crypto trading has two paths, and both are expensive in ways that have nothing to do with performance.

**Path 1: Direct access via managed accounts.** This means opening accounts on each venue the trading team uses, completing KYC on every exchange, setting up API keys and IP whitelists, and granting trading permissions. The trading team will typically only accept this structure with a $1M+ minimum, because operating a sub-account per LP per exchange carries fixed operational cost regardless of ticket size. Performance fee settlement happens via monthly invoice, calculated against a high-water mark that no third party verifies. The allocator is trusting the trading team's NAV math, their HWM accounting, and their willingness to invoice accurately. There is no independent fund administrator in this loop.

**Path 2: A traditional fund vehicle.** Setup costs run into six figures before a single trade is placed: legal entity formation, fund administrator, auditor, custodian, banking relationships, prime broker, regulatory filings. Subscription cycles are monthly or quarterly. Redemption notice periods are 30 to 90 days. Minimums start at $100K and frequently sit at $1M+. Reporting is delivered as a monthly statement, weeks after the period closes.&#x20;

**Path 3\*:** Neutral Trade's Neutral Strategy Vaults, replace the entire stack above with a stablecoin deposit on Solana. Access the same strategy types: cross-exchange arbitrage, funding rate capture, CTA, volatility arbitrage, mid-frequency market making, through audited smart contracts. NAV is calculated on-chain with daily updates. Performance fees are charged automatically against your individual high-water mark, per wallet, with no commingled accounting and no shared loss carry-forward. Minimum deposits start at $5 with no accreditation gate.

***

### The trading team problem

The mirror image of the allocator problem exists on the manager side. A systematic trading team with a working strategy and a track record faces a build-vs-trade decision that has very little to do with their edge.

**Path 1:** The separately managed-account path means running an operation: a sub-account per investor per exchange, monthly HWM calculation per LP, monthly invoicing, follow-up on unpaid fees, individual reporting. It works at a $1M+ minimum and breaks below it. It also leaves the trading team exposed on settlement, they have no enforcement mechanism if an LP simply does not pay the performance fee owed.

**Path 2:** The fund path means becoming a fund manager. Legal setup, ongoing compliance, investor relations, capital raising, fund administration oversight, custody arrangements, bank relationships. Work that competes directly with research and execution time, the only activities that actually generate alpha.

**Path 3\*:** Neutral Trade is the strategy marketplace and the operational layer underneath it. Curators offer strategies through Neutral Strategy Vaults and manage capital via API. We handle exchange access (prime relationships with major venues), custody (off-exchange settlement for CEX positions), per-wallet high-water-mark fee automation, sub-account and margin management, depositor onboarding, and reporting. Performance fees settle automatically. No invoicing, no collection risk.

***

### What this changes

The strategies that historically required a $1M ticket, a fund subscription, and a multi-month onboarding now require a wallet and a deposit transaction.&#x20;

The operational stack that historically required a fund manager to spend more time on administration than on alpha now runs as protocol infrastructure.&#x20;

The trust assumptions that historically required taking a trading team's word for their NAV now resolve to on-chain state.

