# Insurance CE — Project Overview

## What This Is

Aceable is building a national insurance continuing education (CE) catalog. We have 5 existing courses (migrated from REI) that cover Life, Health, Property & Casualty content. The goal is to adapt these courses to meet the CE requirements of as many US states as possible, then submit them for regulatory approval and sell them to licensed insurance producers.

Texas is the first state. Everything else follows the same pattern.

---

## The 5 Source Courses

All generic (not state-specific). Built modularly so content can be trimmed for states with lower hour requirements.

| Course Key | Course Name | Default Delivery | Full (L) Hours |
|---|---|---|---|
| GEN.INS-CE-ETH | Insurance Ethics and Insurance Fraud | Classroom Equivalent | 2.7 hrs |
| GEN.INS-CE-LHOPT | Life & Health Insurance Options | Classroom Equivalent | 8.6 hrs |
| GEN.INS-CE-PCPER | Understanding Personal Lines P&C | Classroom Equivalent | 8.2 hrs |
| GEN.INS-CE-LHPRD | Life & Health Products and Compliance | Self-Study | 9.5 hrs |
| GEN.INS-CE-PCCOM | Understanding Commercial P&C | Self-Study | 8.5 hrs |

**Total L-version catalog: ~37 hrs**

ETH always covers the mandatory ethics requirement. The other courses are split by subject area across delivery types.

---

## Two Delivery Types

**Classroom Equivalent** (ETH, LHOPT, PCPER)
- Learner must complete each chapter before advancing (forced progression)
- Each chapter ends with a quiz — must pass at 70% to continue
- Every reading screen has a minimum lockout time (words ÷ 180 = seconds)
- No final exam
- Counts toward the classroom equivalent minimum most states require

**Self-Study** (LHPRD, PCCOM)
- No forced progression
- Final exam at the end (minimum 10 questions per credit hour, 70% to pass)
- Hours calculated from word count
- Counts toward self-study maximum

---

## Texas — The First Build

TX requires 24 CE hours per 2-year renewal:
- Minimum 12 hrs classroom equivalent
- Maximum 12 hrs self-study
- Minimum 3 hrs ethics

**TX content selection** (not all 37 hrs — trimmed to ~24 hrs):

| Course | Type | TX Hours | Chapters Included |
|---|---|---|---|
| GEN.INS-CE-ETH | Classroom Equiv | 2.70 | All 5 chapters |
| GEN.INS-CE-LHOPT | Classroom Equiv | 6.19 | 9 of 13 chapters |
| GEN.INS-CE-PCPER | Classroom Equiv | 4.21 | 6 of 13 chapters |
| GEN.INS-CE-LHPRD | Self-Study | 5.41 | 7 of 11 chapters |
| GEN.INS-CE-PCCOM | Self-Study | 5.36 | 11 of 11 chapters |
| **Total** | | **23.87 hrs** | |

**What's been done for TX:**
- Chapter cuts specified in `states/tx/manifest.md`
- Per-screen lockout times calculated in `states/tx/screen-timing.md`
- Courses built in Jarvis (chapters removed per manifest)
- Quiz questions being written: 20 chapter-end quizzes × 10 questions = 200 questions
- Final exam questions being written: 54 questions (LHPRD) + 54 questions (PCCOM) = 108 questions
- TDI submission pending (fee: $10/credit hr via Sircon)

---

## State Expansion

Manifests exist for all 48 target states (everything except CA, IL, TX). States fall into 4 tiers:

### Tier 1 — Clone TX (4 states): NJ, VT, NC, UT
Same 24 hrs / 12 classroom equiv / 12 self-study structure as TX. Near-zero incremental build work.

### Tier 2 — 24 hrs, full delivery flexibility (~28 states)
ME, NH, RI, PA, DE, MD, WV, SC, GA, AL, MS, TN, KY, AR, LA, SD, OH, MI, MN, ND, NE, WY, ID, WA, AK, HI, NM, DC

No classroom/self-study split mandate. TX content selection (~23.87 hrs) satisfies all of them. Same build pattern as TX, different state notes.

### Tier 3 — Non-standard hour totals (7 states)
MO (16 hrs), VA (16/24 hrs), KS (18 hrs), NV (30 hrs/3-yr), IA (36 hrs/3-yr), MA (45-60 hrs/3-yr), AZ (48 hrs/4-yr)

NV and IA: our ~37 hrs L-version catalog covers the requirement — use more of the reserved content.
MA and AZ: content gap (~8-23 hrs short). Need additional course content built.

### Tier 4 — Blocked: needs state-specific content (9 states)
CT, NY, FL, OK, MT, OR, CO, WI, IN

Each requires mandatory state-specific content (state law, legislative updates, etc.) that our generic courses can't cover. WI and IN have partial launch options for certain producer types.

**Bottom line: 39 states are ready to build with what we have today.**

---

## The Plan

**Phase 1 — Validate in TX** *(in progress)*
Finish the TX build. Get TDI approval. Confirm the quiz/exam/timing approach works in Jarvis.

**Phase 2 — Scale with existing content**
Roll through Tier 1 and Tier 2 states. Same playbook as TX. ~35 states, no new content needed. Build in volume.

**Phase 3 — Higher-hour states**
NV and IA use the full catalog — straightforward. Decide whether MA and AZ are worth building additional generic content for (~11+ hr gap each).

**Phase 4 — State-specific content**
Prioritize Tier 4 states by market size. FL and NY are likely highest value given licensee population.

---

## Key Repo Files

| File | Purpose |
|---|---|
| `AGENTS.md` | How to work in this repo — conventions, formulas, rules |
| `courses/chapter-topics.md` | All 5 courses: every chapter with topics and hours |
| `courses/source-content/` | Source course JSONs (L versions, never modify) |
| `states/tx/manifest.md` | TX chapter-level content selection spec |
| `states/tx/screen-timing.md` | Per-screen lockout times for TX classroom equiv courses |
| `states/<abbrev>/manifest.md` | Content selection spec for every other state |
| `research/state-requirements-matrix.md` | CE requirements for all 48 target states |
| `planning/state-launch-priorities.md` | States grouped by build effort |
| `planning/expansion-narrative.md` | Full narrative on what's ready and what's blocked |

---

## Question Requirements — Verify Before Writing

These items affect scope and should be confirmed before the question-writing phase begins:

**1. Question bank size (high priority — verify for TX first)**
Many states require a randomized question bank 2–3× larger than the actual exam shown, so learners see different questions each attempt. If TX requires a 3× bank, a 54-question exam requires 162 questions written. This has not been confirmed with TDI. Email CE@tdi.texas.gov to verify before writing exam questions.

**2. Proctored self-study exam states (platform issue)**
11 states require self-study final exams to be monitored by a disinterested third party: CT, MA, DC, WV, GA, AL, MS, AR, IA, NV, HI. This is a platform/delivery configuration question, not a content issue — but it must be resolved before launching self-study courses in these states.

**3. Iowa: closed-book exam required**
Iowa is the only state that requires a closed-book self-study final exam. All other states allow open-book. IA exam questions must be knowledge-based — avoid any question style that assumes the learner can look up the answer. Write IA exam questions as a separate set when that state is built.

**4. Classroom equivalent quiz minimums**
TDI and most states do not specify a minimum number of questions per chapter checkpoint quiz. Our standard of 10 questions per checkpoint is a design choice, not a regulatory requirement. Could be reduced to 5 per checkpoint if capacity is a concern without affecting compliance.

---

## Open Items

- [ ] Verify TX question bank size requirement with TDI (CE@tdi.texas.gov) before writing exam questions
- [ ] Complete TX quiz checkpoint questions (20 checkpoints × 10 questions = 200)
- [ ] Complete TX final exam questions (54 questions each for LHPRD and PCCOM)
- [ ] Submit TX courses to TDI via Sircon
- [ ] Confirm TDI approval timeline (email CE@tdi.texas.gov)
- [ ] Resolve proctored exam platform approach for 11 states before launching self-study there
- [ ] Decide build order for post-TX states
- [ ] Decide whether to invest in MA/AZ content gap
- [ ] Identify which Tier 4 state to tackle first
