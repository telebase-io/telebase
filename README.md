# Telebase

**Telecom Intelligence for AI Agents.**

Telebase is a per-query API for carrier and number intelligence, built for fraud and compliance systems that need a telecom signal at decision time, not a batch report. One call returns whether a number is active, which carrier it sits on, its country and its number type, in structured JSON that an agent can act on without a human in the loop.

SIM swap detection is our next signal and is currently in early access. See [SIM swap detection](#sim-swap-detection-early-access) below.

---

## What's live today

| Signal | Description |
|---|---|
| Active status | Whether a number is currently reachable on the carrier network |
| Carrier | The network operator a number belongs to, checked in real time |
| Country | ISO 3166-1 country code for the number |
| Number type | mobile, landline, fixedVoip, nonFixedVoip, tollFree or voicemail |

Every signal above comes back from a single call.

## SIM swap detection (early access)

SIM swap is wired into the API and returns a real `simSwap` field: `SWAPPED`, `NO_SWAP` or `UNKNOWN`. In our current markets (GB, DE, NL, FR) it returns `UNKNOWN` while carrier registration completes in each market. We're not shipping fabricated swap results in the meantime, so today's response is the honest one.

[Request early access](https://telebase.io/contact-us) to be notified when SIM swap detection goes live in your market.

---

## Who it's for

Telebase is designed for systems that need telecom signals at query time, not batch reports:

- **AI fraud agents** running real-time account protection workflows
- **Identity verification platforms** adding carrier and number signals to onboarding checks
- **Compliance teams** who need telecom data as part of KYC and AML processes
- **Developers** building fraud tooling who want a clean, reliable telecom data API

---

## Pricing

**$0.05 per successful query**, covering every signal in one call.

- Start with 100 free queries when you sign up.
- No annual commitment. No monthly fee. No subscription.
- Pay only for successful lookups.
- Larger volumes are priced lower on request.

You don't need to run your own carrier registration and use case review with each network operator, which typically takes weeks to months per market. See [pricing](https://telebase.io/pricing) for details, or [get in touch](https://telebase.io/contact-us) to arrange credits.

---

## Coverage

Current markets:

- Great Britain (GB)
- Netherlands (NL)
- France (FR)
- Germany (DE)

Expanding to further European markets. [Contact us](https://telebase.io/contact-us) if you need a specific market prioritised.

---

## Quick start

### 1. Sign up

Create an account at [telebase.io](https://telebase.io) to get your API key and 100 free queries.

### 2. Make your first query

```bash
curl -s 'https://telebase.fatcatremote.com/api/lookup?phone=%2B447700900000' \
  -H 'Authorization: Bearer tb_live_xxxxxxxxxxxxxxxxxxxxxxxx'
```

The phone number is E.164 with the leading `+` URL-encoded as `%2B`.

### 3. Parse the response

```json
{
  "phoneNumber": "+447700900000",
  "active": true,
  "carrier": "EE",
  "country": "GB",
  "numberType": "mobile",
  "simSwap": "UNKNOWN",
  "simSwapAt": null,
  "_meta": { "activeSource": "LINE_STATUS" }
}
```

- `active` is a boolean or `null` (`null` means the provider couldn't tell).
- `carrier` and `country` are strings or `null`.
- `numberType` is one of: `mobile`, `landline`, `fixedVoip`, `nonFixedVoip`, `tollFree`, `voicemail`.
- `simSwap` is `SWAPPED`, `NO_SWAP` or `UNKNOWN`. `simSwapAt` is only set when `simSwap` is `SWAPPED`.
- `_meta.activeSource` is `LINE_STATUS` (network-level check) or `VALID` (format-only check).

---

## Designed for AI agents

Telebase is built API-first for agent workflows. Each query is stateless, low-latency and returns structured JSON, so it drops into any agent pipeline, whether that's LangChain, a custom orchestration layer or a proprietary fraud engine.

A typical agent workflow looks like:

1. User initiates a high-risk action (withdrawal, password reset, account change).
2. Agent calls Telebase with the user's registered phone number.
3. Telebase returns carrier, number type and active status in real time (SIM swap status once early access opens in your market).
4. Agent uses the signal as part of its risk scoring decision.

No human in the loop required.

---

## Documentation

Full API reference and response field definitions: [telebase.io/skills-md](https://telebase.io/skills-md).

---

## Get in touch

- Website: [telebase.io](https://telebase.io)
- Request access: [telebase.io/contact-us](https://telebase.io/contact-us)
- Email: [hello@telebase.io](mailto:hello@telebase.io)
- LinkedIn: [Telebase on LinkedIn](https://www.linkedin.com/company/telebase/)
- X / Twitter: [@telebase_io](https://x.com/telebase_io)

If you're building a fraud or compliance system and want to discuss early access or a custom integration, reach out directly.

---

*Telebase is built by a team with years of telco infrastructure experience.*
