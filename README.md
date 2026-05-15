**Real-time telecom intelligence API for AI fraud agents and automated compliance workflows.**

Telebase provides per-query access to carrier-level data — SIM swap detection, HLR lookups, number portability, and more — with no contracts, no minimums, and no setup complexity. Built for the way modern fraud and compliance systems actually work: automated, high-volume, and agent-driven.

---

## What Telebase does

| Query type | Description |
|---|---|
| SIM swap detection | Check whether a mobile number has had a recent SIM change, a primary signal for account takeover fraud |
| HLR lookup | Validate whether a number is live, identify its current network, and detect roaming status |
| Carrier verification | Confirm the network a number belongs to in real time |
| Number portability | Detect whether a number has been ported between carriers |

---

## Who it's for

Telebase is designed for systems that need telecom signals at query time, not batch reports:

- **AI fraud agents** running real-time account protection workflows
- **Identity verification platforms** adding SIM swap as a risk signal
- **Compliance automation** requiring carrier-level data for KYC and AML processes
- **Developers** building fraud tooling who need a clean, reliable telecom data API

---

## Pricing

**$TBD per query.**

No contract. No minimum spend. No monthly fees. You load credit and pay only for what you use. First query can be live in minutes.

---

## Coverage

Current live coverage:

- Great Britain (GB)
- Netherlands (NL)
- France (FR)
- Germany (DE)

Expanding coverage: additional European markets and beyond. [Contact us](mailto:hello@telebase.io) if you need a specific market prioritised.

---

## Quick start

### 1. Sign up and load credit
Create an account at [telebase.io](https://telebase.io) and add prepaid credit. No approval process, no sales call required.

### 2. Make your first query

```bash
curl -X POST https://api.telebase.io/v1/sim-swap \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"phone_number": "+447911123456"}'
```

### 3. Parse the response

```json
{
  "phone_number": "+447911123456",
  "sim_swapped": true,
  "swap_date": "2026-05-10T14:23:00Z",
  "carrier": "EE",
  "country": "GB"
}
```

---

## Designed for AI agents

Telebase is built API-first with AI agent workflows in mind. Each query is stateless, low-latency, and returns structured JSON, making it straightforward to integrate into any agent pipeline, whether you're running LangChain, a custom orchestration layer, or a proprietary fraud engine.

A typical agent workflow looks like:

1. User initiates a high-risk action (withdrawal, password reset, account change)
2. Agent calls Telebase with the user's registered phone number
3. Telebase returns SIM swap status and carrier data in real time
4. Agent uses the signal as part of its risk scoring decision

No human in the loop required.

---

## Documentation

Full API reference, authentication guide, error codes, and integration examples at [docs.telebase.io](https://docs.telebase.io).

---

## Get in touch

- Website: [telebase.io](https://telebase.io)
- Email: [hello@telebase.io](mailto:hello@telebase.io)
- LinkedIn: [Telebase on LinkedIn](https://linkedin.com/company/telebase)

If you're building a fraud or compliance system and want to discuss early access or a custom integration, reach out directly.

---

*Telebase is built by a team with years of telco infrastructure experience. We understand carrier data because we've worked inside the networks.*
