# Phase 1 Plan — Prototype Demo (~64 person-hours, two presets)

**North star:** A **prototype** judges can **see** settle on Stellar — two scripted scenarios, one flow.  
**Quality bar:** Demo/prototype — **not** production readiness.  
**Track:** General Track · **Deadline:** Passport submit by **5 Oct 2026, 16:00 −06**

### Capacity

| | |
| --- | --- |
| **Baseline** | **4 people × ~4 h/day × ~4 sessions ≈ 64 person-hours** |
| **Upside** | Longer sprint = optional extras only |
| **Product rule** | One escrow path; **Food** + **US→Chile** presets (params + copy) |
| **Architecture** | **Simplest thing that demos** — clean contract/oracle split **only if need be**, not a requirement |

Aligned with [`project-context.md`](./project-context.md) and [`hackathon-overview.md`](./hackathon-overview.md).

---

## Prototype posture

| Do | Don’t |
| --- | --- |
| Scripted food + US→Chile scenarios | Aim for production readiness |
| Fake/demo keys, mocks, seed data | Auth hardening, tenancy, observability |
| Compress multi-day time in the UI | Real customs oracle / multi-milestone chain |
| Polish only until it “looks real in ~2 min” | Scalability theater / forced module split |
| One shared settle path | Two products or two contracts |

---

## What we will demo

1. **Prototype stack:** Soroban escrow on testnet + demo keypair check-in + minimal glue + UI (not two products; not production).  
2. **Preset A — Food:** minutes-scale SLA → create → check-in → on-time or late auto refund.  
3. **Preset B — Package US→Chile:** multi-day SLA → same flow; customs/in-transit as **pitch story**; settle stays **time-based**.  
4. **Outcomes:** on-time / mild late / critical late (shared contract; scripted runs OK).  
5. **~2 min live script** hits both presets + tx/Explorer proof; ≤3 min pitch video.

---

## Scope

### In scope (~64h)

| Piece | Behavior |
| --- | --- |
| **Soroban escrow** | Shared contract; 2–3 outcomes from deadline params |
| **Demo attestation** | Keypair-signed check-ins (SE stand-in); fake keys OK |
| **Glue** | create / attest / settle — thin REST **and/or** scripts; whatever is fastest |
| **Demo UI** | Preset switcher Food \| Package US→Chile; check-in + status/refund |
| **Testnet + script** | Rehearsed ~2 min covering **both** presets |

### Preset params (illustrative)

| Preset | Copy | `deadline` | Mild window | Mild refund |
| --- | --- | --- | --- | --- |
| Food | “Burger Combo · local delivery” | now + **30 min** | +**15 min** | ~20% |
| Package US→Chile | “Electronics · US → Chile” | now + **7 days** (simulate +N days via attest ts) | +**2 days** | ~20% |

### Out of scope (baseline)

- Real Secure Enclave / mobile SDKs  
- Full multi-milestone customs chain / real customs oracle  
- Production multi-tenant B2B, auth hardening, tenancy, observability  
- Separate food vs package apps/contracts  
- Mandated clean architecture / “scalability” scaffolding  

### Optional (upside only)

- Geofence; merchant webhook; `reason: customs_hold`  
- Extract a separate oracle helper **if** it happens to be convenient — never block the demo for it  

---

## Team split (~16 h each — merge if simpler)

| Role | Focus | Notes |
| --- | --- | --- |
| **Contract** | Escrow + tiers + testnet deploy | Required |
| **Signing + glue** | Demo keypair + create/attest/settle wiring | May live next to UI or as tiny REST |
| **Demo UI** | Presets + check-in + status | Looks-real-enough polish only |
| **Pitch + deploy** | Scripts, README, 2-min dual script, video, Passport | Fake keys / seed docs OK |

---

## Milestones (4 sessions)

### Session 1 — Skeleton & presets (~16 h)

- Pick simplest glue shape (don’t bikeshed folders)  
- Contract: `create_delivery` with deadline/mild params  
- Preset map (food / package → numbers + labels)  
- UI: preset picker shells  
- Passport register; README says “prototype”  

**Exit:** both presets selectable; mocks OK.

### Session 2 — Happy path (~16 h)

- On-time settle on testnet (food first)  
- Wire create → attest → settle somehow  
- UI: escrowed → delivered  

**Exit:** one live on-time path.

### Session 3 — Dual scenarios + late (~16 h)

- Mild + critical late  
- Package preset with time compression  
- Customer refund/discount visible for both  
- Smoke both presets (scripted)  

**Exit:** both presets demoable.

### Session 4 — Rehearse & submit (~16 h)

- Dual-preset live script ×2; backup recording  
- Pitch: food + US→Chile (customs = story)  
- Passport submit — freeze features  

Optional only after Session 3 green.

---

## Suggested repo structure (opportunistic)

Prefer flat/simple. Example — **collapse freely**:

```text
logichain/
├── README.md                 # “prototype / demo”
├── docs/pitch-outline.md
├── contracts/…               # Soroban escrow
├── web/                      # demo UI (+ glue if colocated)
├── server/ or scripts/       # optional REST / invoke helpers
└── scripts/fund-and-deploy.sh
```

Do **not** invent `oracle/` + `api/` packages just to look scalable.

---

## Contract surface (keep small)

Enough for the demo (names flexible):

- `create_delivery(…, deadline_ts, mild_secs, mild_refund_bps)`  
- `submit_attestation(…, delivered_at_ts, signature)` **or** trusted demo caller if signing inline is simpler  
- `settle → OnTime | PartialRefund | FullRefund`  

Trusted demo admin / skip fancy sig verify is OK if it ships the prototype faster — call it out honestly in README.

---

## Demo script (~2 min live)

1. **Food (≈50s):** Food preset → create → late check-in → refund + tx.  
2. **Package US→Chile (≈50s):** Switch preset → create → simulate +N days → refund; one line on customs/in-transit as SLA blow.  
3. **Close (≈20s):** Optional on-time flash; Explorer link.

### Pitch video (≤3 min)

Hook → live food late → live package late → why Stellar → “prototype today; SE / richer customs later.”

---

## Success criteria

- [ ] Testnet escrow with on-time + late (scripted OK)  
- [ ] Two presets on one flow (food minutes, US→Chile days)  
- [ ] Demo keypair (or trusted demo) check-in path  
- [ ] ~2 min dual-preset demo + ≤3 min pitch  
- [ ] Open-source repo + General Track submission  
- [ ] No time wasted on auth/tenancy/observability/forced architecture  

---

## Risks

| Risk | Mitigation |
| --- | --- |
| Building two products | Presets only |
| Over-engineering glue | Colocate; skip REST if scripts+UI suffice |
| “Clean split” eats hours | Optional only; demo wins |
| Multi-day hard live | Attest timestamp / +N days control |
| Customs scope creep | Pitch story only |
| Behind on hours | Drop mild tier before second preset |
