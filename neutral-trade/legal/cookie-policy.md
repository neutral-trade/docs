# COOKIE POLICY

**Last updated:** 2026-07-25

This Cookie Policy explains how Neutral Trade ("**we**", "**us**", or "**our**") uses cookies, browser local storage, and similar technologies on the website at **https://www.neutral.trade**, any associated mobile applications, and any related interfaces operated by Neutral Trade (collectively, the "**Interface**").

This Policy supplements our **Privacy Policy**, available at [https://docs.neutral.trade/legal/privacy-policy](https://docs.neutral.trade/legal/privacy-policy), which describes how we process personal data more generally. Section 5 of the Privacy Policy summarises our use of cookies; this Policy provides the detail. Where this Policy and the Privacy Policy conflict, **the Privacy Policy prevails**.

If you have questions about this Policy, contact us at **privacy@neutral.trade**.

### 1. What cookies and similar technologies are

Cookies are small text files placed on your device by a website. We also use **browser local storage**, which serves a similar purpose but stores data in your browser rather than sending it with each request. In this Policy, references to "cookies" include local storage and similar technologies unless stated otherwise.

We group these technologies into two categories:

* **Strictly necessary** — required to operate the Interface, apply geographic restrictions, remember your preferences, and record the choices you have made (including your cookie choice itself). These are set without consent because the Interface cannot function correctly without them.
* **Analytics** — used to understand how the Interface is used so we can improve it. These are **optional**. We ask for your consent before enabling them, and you may decline.

We do not use cookies for advertising, and we do not share cookie data for cross-context behavioural advertising.

### 2. First-party cookies

| Name             | Category           | Purpose                                                                                          | Retention                               |
| ---------------- | ------------------ | ------------------------------------------------------------------------------------------------ | --------------------------------------- |
| `NEXT_LOCALE`    | Strictly necessary | Stores your selected interface language                                                          | Up to 12 months                         |
| `nt_geo_country` | Strictly necessary | Stores a coarse country code derived from your connection, used to apply geographic restrictions | Session; refreshed on each page request |
| `nt_geo_blocked` | Strictly necessary | Stores whether geographic restrictions apply to your session (`0` / `1`)                         | Session; refreshed on each page request |

These cookies are set with `path=/` and `SameSite=Lax`, and with the `Secure` attribute in production.

### 3. Browser local storage

| Key                              | Category           | Purpose                                                                                          |
| -------------------------------- | ------------------ | ------------------------------------------------------------------------------------------------ |
| `nt_cookie_consent`              | Strictly necessary | Records your cookie choice so that we do not ask again                                           |
| `neutral-trade-acknowledgements` | Strictly necessary | Records that you have acknowledged required notices, with timestamps                             |
| `neutral-trade-geo-block`        | Strictly necessary | Holds the geographic restriction state used by the Interface                                     |
| `referral-store`                 | Strictly necessary | Holds referral or invite codes from links you follow, with expiry information                    |
| `neutral-trade-bookmarks-v2`     | Strictly necessary | Holds the strategies you have bookmarked in the Interface                                        |
| `theme`                          | Strictly necessary | Holds your light, dark, or system display preference                                             |
| `nt_api_key_v1`                  | Strictly necessary | Set **only** on our API documentation page; holds an API key you enter in order to test requests |
| `ph_*`                           | Analytics          | Analytics identifiers and state, written **only** if you consent to analytics (see §4)           |
| `__ph_opt_in_out_*`              | Strictly necessary | If you decline analytics, a single flag recording that analytics is disabled                     |

Clearing local storage may reset your language, display preference, acknowledgements, and saved items.

### 4. Analytics

We use **PostHog**, hosted in the European Union, to measure how the Interface is used — for example pages viewed, features used, and errors encountered. Analytics requests are routed through our own domain to PostHog's EU infrastructure.

Analytics is consent-based and behaves as follows:

* **Before you choose** — analytics runs without cookies or persistent identifiers. Nothing is stored in your browser, and no identifier follows you between visits.
* **If you accept** — PostHog stores an identifier in a cookie and in local storage (the `ph_*` keys above) so that we can understand usage across visits.
* **If you decline** — analytics collection is switched off in your browser and no analytics identifiers are written. The only item stored is the flag that keeps analytics disabled.

Further information is available in PostHog's privacy policy at [https://posthog.com/privacy](https://posthog.com/privacy).

### 5. Third-party services

Some features of the Interface are provided by third parties that may set their own cookies or storage under their own policies. Their use of your data is governed by those policies, not this one.

#### 5.1 Wallet connectivity

The Interface integrates **Reown** (the WalletConnect ecosystem) for wallet connection, optional email and social sign-in, swaps, and fiat on-ramp features.

* Privacy policy: [https://reown.com/privacy-policy](https://reown.com/privacy-policy)
* Cookie policy: [https://reown.com/cookie-policy](https://reown.com/cookie-policy)
* Terms of service: [https://reown.com/terms-of-service](https://reown.com/terms-of-service)

#### 5.2 Identity providers

Where you choose to sign in using a third-party account, that provider processes the relevant authentication data under its own policy:

| Provider    | Privacy policy                                                                                                                                                 |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Google      | [https://policies.google.com/privacy](https://policies.google.com/privacy)                                                                                     |
| X (Twitter) | [https://x.com/privacy](https://x.com/privacy)                                                                                                                 |
| Discord     | [https://discord.com/privacy](https://discord.com/privacy)                                                                                                     |
| GitHub      | [https://docs.github.com/site-policy/privacy-policies/github-privacy-statement](https://docs.github.com/site-policy/privacy-policies/github-privacy-statement) |

#### 5.3 Hosting

The Interface is hosted on **Vercel**, which processes technical data such as IP addresses in order to serve the Interface and provides the coarse country signal described in §2.

* Privacy policy: [https://vercel.com/legal/privacy-policy](https://vercel.com/legal/privacy-policy)
* Data processing addendum: [https://vercel.com/legal/dpa](https://vercel.com/legal/dpa)

### 6. Your choices

* When you first visit the Interface, a notice allows you to **accept** or **decline** analytics. Strictly necessary technologies are not affected by this choice.
* To change a choice you have already made, clear this site's data in your browser settings. The notice will appear again on your next visit.
* You can block or delete cookies at any time through your browser settings.
* Where processing is based on consent, you may withdraw that consent at any time without affecting the lawfulness of processing carried out beforehand, as described in §6 of the Privacy Policy.

Blocking or clearing **strictly necessary** cookies and local storage may impair the functioning of the Interface, including language selection, geo-restriction logic, and wallet connectivity.

### 7. Changes to this Policy

If our use of cookies changes, we will update this Policy and revise the date above. Where the change is material, we will use reasonable means to notify you, such as a notice on the Interface.

### 8. Contact

For any questions about this Cookie Policy, contact us at **privacy@neutral.trade**.
