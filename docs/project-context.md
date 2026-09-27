# LogiChain API — Project Context

Durable context for the Hackathon Stellar project. Complements [`logichain-brief.md`](./logichain-brief.md) and [`hackathon-overview.md`](./hackathon-overview.md). Execution plan: [`phase-1-plan.md`](./phase-1-plan.md).

---

## Build constraints (authoritative for this sprint)

| Constraint | Value |
| --- | --- |
| Team | **4 people** |
| Cadence | **~4 hours per person per day**, across **~4 sessions** |
| Baseline budget | **~64 person-hours** (4 × 4 h × 4 days) |
| Optional upside | Longer sprint sometimes plausible — **bonus**, not the plan |
| Event calendar | Passport submit by **5 Oct 2026, 16:00 −06**; optional TEC Cartago meetup 30 Sep |
| Priority | **Prototype / demo** — bar is “looks real in a ~2 min demo,” **not** production readiness |
| Product rule | **Do not build two products** — one escrow flow; two **presets** (food + US→Chile) |
| Architecture | Prefer the **simplest thing that demos**; clean contract/oracle split **only if needed** — not mandated |

---

## Prototype posture (bar for quality)

This is **mainly a prototype**. Explicitly OK / expected:

- Scripted scenarios (food + US→Chile presets)
- Fake/demo keys, mocks, seed data, hard-coded accounts
- Compress multi-day package time via UI / attest timestamp overrides
- Skip auth hardening, tenancy, observability, CI perfection, polish beyond “looks real in 2 minutes”

**Not** the bar: production readiness, multi-tenant B2B, real Secure Enclave, full customs chain.

**Opportunistic only:** if a thin contract ↔ signing helper split falls out naturally and costs almost nothing, fine — do **not** spend hours on “scalability theater.”

---

## Problem

Delivery platforms (q-commerce and parcel) burn money and trust on **manual dispute handling** for late deliveries — whether a meal is 40 minutes late or a package sits days past SLA.

1. **Support friction:** Refunds/discounts go through human agents → high OpEx, inconsistent outcomes.
2. **Attestation gap (future):** Soft GPS / status updates can be gamed; hardware attestation is the long-term fix — **mocked** this sprint via demo keypair.
3. **Wrong chain economics:** High-gas L1s make per-shipment escrow uneconomic → **Stellar / Soroban**.

---

## Solution (vision vs this prototype)

**Vision (brief):** B2B API: escrow + attested time/geo → automatic refunds.

**This prototype (~64h):** One Soroban escrow on **testnet** plus whatever minimal glue gets a **demo UI** showing **two presets** (same settle mechanics, different SLA params + copy):

| Preset | Story | SLA shape |
| --- | --- | --- |
| **Food delivery** | Local q-commerce | Minutes (e.g. 30 min) |
| **Package delivery** | Product **US → Chile** | Multi-day delay story |

Package pitch may **mention** customs / in-transit delay; on-chain logic stays **time-based** (no real customs oracle unless leftover hours and clearly optional).

Glue can be: thin REST, or UI talking more directly to scripts/contract — **whichever is fastest** to demo both presets.

---

## Stack (prototype)

| Layer | Choice | Role |
| --- | --- | --- |
| Settlement | **Soroban**, Stellar **testnet** | Escrow + 2–3 time-based outcomes |
| Attestation | Demo **keypair-signed** check-in (SE stand-in) | Fake keys OK |
| Glue | Minimal (REST and/or scripts) | create / attest / settle |
| Show | **Demo UI** | Preset picker + check-in + status / refund |
| Assets | Testnet XLM (or test USDC) | Fastest path |

---

## Architecture (illustrative — simplify freely)

Logical flow (folders/modules optional):

```
Demo UI (preset: Food | Package US→Chile)
  → create / attest / settle (API and/or scripts)
  → signed check-in (demo keypair)
  → Soroban escrow (same contract, different deadline params)
        ├─ on-time      → full payout
        ├─ mild late    → partial refund
        └─ critical late → full refund
```

- **Required:** one contract path; two presets via params + copy.  
- **Not required:** separate `oracle/` vs `api/` packages, microservice boundaries, or “clean interfaces for scale.”  
- **Optional upside:** geofence; merchant webhook; `reason: customs_hold` string — still time-based settle.

---

## Goals

| Horizon | Goal |
| --- | --- |
| This sprint | Prototype that demos both presets on testnet; ~2 min script; ≤3 min pitch |
| Stories | Food (minutes) **and** US→Chile package (days) |
| Non-goals | Production quality, auth/tenancy/observability, real SE, multi-milestone customs |

---

## Use cases (demo presets)

| Preset | Narrative | Params (illustrative) |
| --- | --- | --- |
| Food / q-commerce | Burger order, 30-min SLA | `deadline` ≈ now+30m; mild +15m @ ~20% |
| Package US→Chile | Parcel to Chile, multi-day SLA | `deadline` ≈ now+7d (demo clock compress OK); mild +2d @ ~20% |

Same settle path for both.

---

## Scope summary

### In scope (~64h prototype)

- Single Soroban escrow (2–3 outcomes)
- Demo keypair check-ins (SE stand-in)
- Minimal glue + demo UI with **two presets**
- Stellar testnet + scripted ~2 min demo (both scenarios)
- Mocks, seed data, fake keys

### Out of scope (baseline)

- Real Secure Enclave / mobile SDKs  
- Full multi-milestone customs chain / real customs oracle  
- Production multi-tenant B2B, auth hardening, tenancy, observability  
- Two separate apps or contracts  
- Mandated clean architecture / scalability scaffolding  

### Optional (upside only)

- Simple geofence; merchant webhook; attestation `reason` string  
- Slightly cleaner module split **if** it doesn’t slow the demo  

---

## Open decisions

| Decision | Default | Status |
| --- | --- | --- |
| Escrow asset | Testnet XLM | Session 1 |
| Mild refund | ~20% | Locked |
| Package demo clock | Attest timestamp / “+N days” control | Locked |
| Glue shape | Simplest that works (REST optional) | Opportunistic |
| Track | **General Track** | Locked |

---

## Map to hackathon

| Constraint | Fit |
| --- | --- |
| Must use Stellar | Testnet Soroban escrow + two SLA presets |
| General Track | Local + cross-border commerce story |
| Judging | Working prototype demo > unfinished “platform” |
| Submission | Open-source repo + ≤3 min pitch by 5 Oct |

---

## Team shape

Rough lanes: **contract** / **signing + glue** / **demo UI** / **pitch + deploy** — merge lanes if simpler. See [`phase-1-plan.md`](./phase-1-plan.md).
