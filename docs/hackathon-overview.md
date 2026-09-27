# Find Your Way Hackathon — Overview

**Source of truth:** [Luma event](https://luma.com/9h5jl18k) · [Stellar Passport hackathon](https://demo.stellarpassport.xyz/hackathons/find-your-way-meridian-hackathon) · [Costa Rica Passport event](https://demo.stellarpassport.xyz/events/stellar-chile/find-your-way-hackathon-costa-rica)  
**Researched:** 2026-09-24 · Passport status at research time: `submissions_open` (~81 participants)

---

## Snapshot

| Field | Detail |
| --- | --- |
| Name | Find Your Way: Hackathon (Costa Rica chapter) |
| Platform | Stellar Passport |
| Goal | Hands-on Stellar build + pitch practice ahead of **HackMeridian** (Lisbon, 25–26 Oct 2026) |
| Prize pool | **5,000 USDC** |
| Teams | 1–5 people |
| Tech requirement | Project must **use Stellar** (or contribute meaningfully to its ecosystem) |
| Format | Remote build + optional in-person meetup; submit via Passport |

---

## Dates

| Milestone | When |
| --- | --- |
| Registration opens | 1 Sep 2026 |
| Submissions open | 21 Sep 2026 |
| **In-person meetup (TEC Cartago)** | **30 Sep 2026**, ~5:00–8:00 p.m. local (provisional 6–8 p.m. on Luma; schema dates 17:00–20:00 −06:00) |
| **Submission deadline** | **5 Oct 2026, 4:00 p.m.** (Costa Rica / −06) ≈ `2026-10-05T22:00:00.000Z` |
| Judging window ends | ~9 Oct 2026 |
| Results published | **12 Oct 2026, 6:00 p.m.** |

Hard deadline for LogiChain: ship open-source repo + ≤3 min pitch video by **5 Oct**.

---

## Location & format

- **Venue / community hub:** Costa Rica Institute of Technology (TEC), Cartago campus — Dulce Nombre, Cartago.
- **Build mode:** Primarily asynchronous (register → team → build on Stellar → submit on Passport).
- **Meetup:** Optional in-person session at TEC Cartago (networking / community points on Passport).
- **Downstream event:** HackMeridian 2026 — ONE16, Lisbon; Genesis (idea→MVP) and Scale (prototype→product); prizes up to ~$30k XLM; AI tooling explicitly allowed.

---

## Tracks, prizes & eligibility

### General Track — $4,000 USDC

Open to builders whose projects use Stellar or contribute to the ecosystem. Suggested domains from Passport: payments, financial inclusion, tokenization, **smart contracts**, developer tools, wallets, identity, **commerce**, education, public goods.

| Place | Amount (USDC) |
| --- | --- |
| 1st | 2,000 |
| 2nd | 1,000 |
| 3rd | 500 |
| Honorable mention ×2 | 250 each |

**Recommended track for LogiChain** (commerce + Soroban escrow / conditional settlement).

### University Track — $1,000 USDC

- Two awards of **$500 USDC**.
- **Eligibility:** currently enrolled at a **university in Chile**, with proof of enrollment.
- Pitch must cover problem, solution, how it works, and Stellar usage.

> Costa Rica–based student teams without Chile enrollment should submit under **General Track**.

---

## Sponsors & organizers (esp. Stellar)

| Role | Who |
| --- | --- |
| Chain / ecosystem | **Stellar** (build requirement + docs resource) |
| Platform | **Stellar Passport** (registration, teams, submissions, points) |
| Local organizers (Luma) | **Tellus Cooperative**, ZEEK |
| Venue | **TEC Cartago** (Costa Rica Institute of Technology) |
| Passport path | Nested under Stellar Chile event routes; regional “Find Your Way → HackMeridian” funnel |
| Next step | **HackMeridian / Meridian** (Stellar conference ecosystem, Lisbon) |

Public materials emphasize Stellar as the required stack; SDF is the broader ecosystem sponsor via Passport / HackMeridian, not listed as a separate Costa Rica prize sponsor beyond USDC prizes on Passport.

---

## Judging criteria (General Track)

From Passport track description:

1. **Technical execution**
2. **Meaningful use of Stellar**
3. **Originality**
4. **Potential impact**
5. **User experience**
6. **Presentation quality**

No numeric rubric weights published. Prioritize a working Stellar/Soroban demo + clear pitch over a wide unfinished surface area.

---

## Submission requirements

Submit on Stellar Passport before the deadline. Schema fields:

| Field | Required | Notes |
| --- | --- | --- |
| Project name | Yes | Public title |
| Project description | Yes | |
| Submission track | Yes | General or University |
| Email | Yes | |
| **Repo link** | Yes | **Must be open source** |
| **Video pitch** | Yes | **Max 3 minutes** |
| Other links | No | Demo, docs, Explorer txs, etc. |
| Passport T&Cs | Yes | Checkbox |

### How to register (do not skip steps)

1. Create Stellar Passport account: https://demo.stellarpassport.xyz/auth/signup  
2. Register on the hackathon page and join/create a team: https://demo.stellarpassport.xyz/hackathons/find-your-way-meridian-hackathon  
3. (Optional / points) Check into Costa Rica event: https://demo.stellarpassport.xyz/events/stellar-chile/find-your-way-hackathon-costa-rica  
4. Build on Stellar → complete delivery in-platform before close.

Creating a Passport account alone does **not** enroll you.

---

## Tech constraints & resources

- **Must use Stellar** (Classic payments and/or **Soroban** smart contracts).
- Official resource linked by organizers: [docs.stellar.org](https://docs.stellar.org).
- Repo must be public/open source at submission.
- No other hard stack bans published (Node/Go APIs, mobile SDKs, oracles OK if Stellar is central).
- HackMeridian (follow-on) explicitly encourages AI coding tools (Cursor, agents, etc.).

---

## Gaps / verify before submit

- Exact meetup agenda and confirmed 6–8 p.m. vs 5–8 p.m. window.
- Whether University Track Chile rule applies unchanged to the Costa Rica chapter (Passport API still says Chile).
- Prize payout wallet / KYC process (not in public schema).
- Whether live demo URL is expected beyond repo + video (optional “other links” only).

---

## Implications for LogiChain

- Target **General Track**.
- Deadline pressure: ~11 days from research date to submission close → **Phase 1 = Soroban MVP + demo narrative**, not full mobile Secure Enclave / production oracle.
- Judges reward **meaningful Stellar use** → on-chain escrow + time/geo penalty logic must be real and demoable (testnet txs).
- Pitch video ≤3 min: problem → escrow flow → live settlement outcomes → why Stellar fees/finality matter for logistics.
