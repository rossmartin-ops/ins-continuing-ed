# AGENTS.md — Insurance Continuing Education Repo

This repo is the planning and build source for Aceable's insurance continuing education (CE) catalog. It supports building CE course packages for multiple states. TX is the first state; many more will follow using the same patterns.

Read this file before doing anything else in this repo.

---

## What This Repo Is For

Each state has its own CE requirements — total hours, delivery method rules, ethics requirements, etc. We have 5 existing source courses (exported from Jarvis) that together cover Life, Health, Property & Casualty content. The job of this repo is to:

1. Document what's in the source courses
2. Define state-specific content selections (which levels/chapters to include)
3. Specify the build requirements (quizzes, exams, timed screens) per state
4. Serve as the source of truth for what gets built in Jarvis

---

## Repo Structure

```
/courses
  /source-content       - Full L-version Jarvis course JSONs (source of truth, never modify)
  overview.md           - L-version hour and structure reference for all 5 courses
  chapter-topics.md     - Chapter-level topic summaries and hours for all 5 courses

/states
  /<state-abbreviation>
    manifest.md         - Content selection, hour totals, and build requirements for that state

/research
  tx-requirements.md              - TX-specific regulatory rules
  tx-ins-ce-course-recommendation.md  - Original LX recommendation doc for TX

/planning
  h1-2026-scope.md      - TX H1 2026 scope, open questions, resolved questions
```

---

## The 5 Source Courses

All courses are the "L" (large/full) version. They were built modularly — content can be trimmed by dropping levels or chapters for states with lower hour requirements.

| Course Key | Course Name | Delivery (default) | L-Version Hrs |
|---|---|---|---|
| GEN.INS-CE-ETH | Insurance Ethics and Insurance Fraud | Classroom Equivalent | 2.7 |
| GEN.INS-CE-LHOPT | Life & Health Insurance Options | Classroom Equivalent | 8.6 |
| GEN.INS-CE-PCPER | Understanding Personal Lines P&C | Classroom Equivalent | 8.2 |
| GEN.INS-CE-LHPRD | Life & Health Products and Compliance | Self-Study | 9.5 |
| GEN.INS-CE-PCCOM | Understanding Commercial P&C | Self-Study | 8.5 |

- GEN.INS-CE-ETH always covers the ethics/consumer protection requirement
- All 5 together = ~37 hrs of content (more than any single state needs)
- Course structure in Jarvis: Course → Levels → Chapters → Pages
- All screens are currently FULL_SCREEN reading nodes — no quiz infrastructure exists in any course

---

## Hour Calculation

**TDI Basic formula (used as the standard across this repo):**

> credit hours = words ÷ 180 ÷ 50

- 180 = average reading speed (WPM) per TDI Basic level definition
- 50 = minutes per credit hour (1 credit hour = 50 minutes of instructional time)
- Final exams and pre-tests do NOT count toward instructional time

Apply this formula to word counts extracted from the course JSON `html` fields (strip HTML tags before counting).

---

## Delivery Method Rules

### Classroom Equivalent
- Forced unit progression (learners cannot skip chapters)
- Embedded quiz at the end of each included chapter (minimum 70% to pass before advancing)
- Reading screens must be timed — each screen enforces a minimum lockout based on its word count at 180 WPM
- The timed reading screens + quiz completion time = the source of countable CE hours
- No final exam required

### Self-Study
- No forced progression
- Final exam required: minimum 10 questions per credit hour, 70% passing score
- No proctoring required
- Hours come from word count (Basic formula above)

---

## How to Create a State Manifest

For each new state, create `states/<state>/manifest.md` using this process:

1. **Get the state's requirements** — total hours, classroom equiv minimum, self-study maximum, ethics requirement, any other constraints
2. **Calculate L-version hours per chapter** — use `chapter-topics.md` as the reference; recalculate with the Basic formula if needed
3. **Select levels and chapters** to hit the state's hour targets — favor content-quality decisions over pure hour math; note reasons for drops
4. **Specify build work** — quiz checkpoint count (classroom equiv) and final exam question count (self-study, 10 per credit hr)
5. **Document available reserve content** — list excluded chapters/levels for future use

### Manifest structure
Each manifest should include:
- State requirements summary
- Per-course table: level, chapter, include/drop, hrs, topics, quiz/exam Qs
- Hours summary (classroom equiv total, self-study total, grand total)
- Build work summary (checkpoint count, exam question count)
- Reserve content table (what's available for higher-hour states)

---

## Hard Rules

- **Never modify source JSON files.** They are the immutable content library.
- **State manifests are specs, not code.** They tell the Jarvis build team what to include — they don't modify anything themselves.
- **Cuts are at level or chapter granularity.** Do not cut individual pages within a chapter.
- **Chapter names in Jarvis are generic** ("Chapter 1", "Chapter 2") and must be renamed when chapters are dropped to maintain correct numbering.
- **The ETH course (GEN.INS-CE-ETH) should always be included as classroom equivalent** — it covers the ethics requirement that virtually every state mandates.
- **Modifications to a course exceeding 25% of content require a new TDI course registration** (and likely equivalent rules in other states). Track this when making cuts.

---

## Key Contacts and Links

- TDI general CE questions: CE@tdi.texas.gov
- TDI course/provider status: CE_Providers@pearson.com
- TDI credit hour calculation: https://www.tdi.texas.gov/agent/education-providers/credit-hour-calculation.html
- TDI course registration: https://www.tdi.texas.gov/agent/education-providers/register-a-ce-course.html
- Jarvis INS CE catalog: https://gvt.jarvishq.com/@ace/content/course/list?query=gen.ins-ce
- LX Plan (Google Sheet): https://docs.google.com/spreadsheets/d/1k8GAM-cTIMV5NPRKpSuatzmwNS4zbAaZyb1bkH6dWj0/edit?gid=1135064916#gid=1135064916
