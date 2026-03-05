# Insurance Continuing Education (CE) Planning

Planning repo for building out Aceable's Insurance CE course catalog, starting with Texas.

## Goal

Launch a 5-course TX Insurance CE package that satisfies the 24-hour requirement for licensed producers and adjusters:

- **12 hours** as classroom equivalent (mandatory minimum)
- **12 hours** as self-study (maximum allowed)

## H1 2026 Scope

The existing 5-course catalog (migrated from REI) will be updated — not expanded. No separate L&H or P&C packages this cycle.

## Course Plan

### Classroom Equivalent (12 hrs minimum) — needs quiz/checkpoint updates

| Course | Word Count | TX Hours (Basic formula) |
|---|---|---|
| Insurance Ethics and Insurance Fraud | 24,792 | 3 hrs |
| Life & Health Insurance Options | 76,963 | 9 hrs |
| Understanding Personal Lines Property & Casualty Insurance | 73,775 | 8 hrs |

Requirements for classroom equivalent:
- Forced unit progression
- Embedded quizzes/interactive checks per unit (pass at 70% to advance)
- Timed content aligned to approved CE hours
- No final proctored exam

### Self-Study (up to 12 hrs) — needs final exam added

| Course | Word Count | TX Hours (Basic formula) |
|---|---|---|
| Life & Health Products and Compliance | 84,319 | 9 hrs |
| Understanding Commercial Property & Casualty Insurance | 75,047 | 8 hrs |

Requirements for self-study:
- Final exam (minimum 10 questions per credit hour)
- 70% passing score
- No forced progression required

## TX Regulatory Reference

- Total required CE: 24 hours per 2-year license term
- Ethics/consumer protection: 3 hours minimum
- Classroom equivalent: at least 12 hours
- Self-study: maximum 12 hours
- 1 credit hour = 50 minutes of instructional time
- Final exams and pre-tests do NOT count toward instructional time

## Repo Structure

```
/courses          - Full L-version course content (source of truth) and overview
/states           - Per-state content manifests defining which levels to include
  /tx             - Texas build: level selections, hours, quiz/exam requirements
/research         - Regulatory research, competitor analysis, TDI references
/planning         - Project plans, timelines, LX capacity notes
```

Source course JSONs are the L (large) versions — the complete content library. State manifests select from these to hit each state's required hours without modifying the source.

## Key Links

- [Jarvis INS CE catalog](https://gvt.jarvishq.com/@ace/content/course/list?query=gen.ins-ce)
- [TDI Credit Hour Calculation](https://www.tdi.texas.gov/agent/education-providers/credit-hour-calculation.html)
- [2025 INS CE Expansion - LX Plan (Google Sheet)](https://docs.google.com/spreadsheets/d/1k8GAM-cTIMV5NPRKpSuatzmwNS4zbAaZyb1bkH6dWj0/edit?gid=1135064916#gid=1135064916)
