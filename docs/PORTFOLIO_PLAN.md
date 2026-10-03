# GitHub Portfolio Improvement Plan

**Author:** Himanshu Patil
**Created:** 2026-10-03
**Status:** Draft — awaiting selection of daily rotation
**Repo:** `HimanshuPatil2001/HimanshuPatil2001` (profile repo, holds this plan)

---

## 0. Why this plan exists

The objective is a daily commit streak on GitHub that reflects **real work**, not
noise. The method is deliberately simple and repeatable so that it can survive a
low-capability model and still produce professional results.

### The operating principle

> **Document everything. If it isn't written down, it didn't happen.**

A model that is not clever can still be *reliable* if every step is traceable to a
document written before the step was taken. The document set is the source of
truth; the code is an implementation detail of the document.

This mirrors how a well-run organisation works:

| Stage | Artefact | Question it answers |
|---|---|---|
| 1. Client request | `docs/01-request/` | What was asked, and by whom? |
| 2. FSD | `docs/02-fsd/` | What will we build? What is out of scope? |
| 3. Code plan | `docs/03-code-plan/` | Which files, which order, which risks? |
| 4. Implementation log | `docs/04-implementation/` | What did we actually do, day by day? |
| 5. Testing | `docs/05-testing/` | What proves it works? |
| 6. Deployment | `docs/06-deployment/` | How does it reach production? |
| 7. Monitoring | `docs/07-monitoring/` | How do we know it is healthy? |
| 8. Handover | `docs/08-handover/` | What does the next person need? |

**The rule that makes this work for a weak model:** a stage may only begin when the
previous stage's document exists. If the document is missing, the work has not
started — regardless of what code exists.

### Non-negotiables

1. **No code without a plan document.** Code written first is rewritten later.
2. **Commit messages reference the document.** Not "update" — `docs: add FSD for X (§02)`.
3. **Every decision is recorded with its reason.** Future readers need *why*, not just *what*.
4. **Secrets never enter a repo.** `.env.example` documents the shape, never the value.
5. **A failed attempt is documented too.** Negative results save the next person a day.

---

## 1. Current portfolio audit

Audited 2026-10-03 via the GitHub API — 15 non-fork repositories.

| Repo | Language | Files | Last push | Gaps |
|---|---|---|---|---|
| Aarohi-Bot | C# | 47 | 2026-09-29 | no CI, no license, no tests |
| Teams-Green | C# | 33 | 2026-09-29 | no CI, no license, no tests |
| Japanese-Test | TypeScript | 39 | 2026-09-29 | no CI, no tests, no license |
| Tracking-Project | Python | 14 | 2026-09-29 | no CI, no tests, no license, no docs |
| Meal_Planner | Python | 9 | 2025-09-17 | **no README**, committed `.pyc`, no license |
| Movies-Recommendation-System | HTML | 12 | 2025-10-03 | no CI, no tests, no license |
| Book_reader_chatbot | Python | 17 | 2025-10-03 | no CI, no license, no docs |
| discord-music-bot | Python | 6 | 2025-09-30 | no CI, no tests, no license |
| WebRoom | JavaScript | 8 | 2025-08-08 | no CI, no tests, no license |
| Gemini_ChatBot | CSS | 22 | 2025-07-27 | no CI, no license, no docs |
| Hotel-Review-System | Notebook | 8 | 2023-02-08 | **no README**, no CI, no license |
| Gold-Price-Forecasting | Notebook | 7 | 2023-02-08 | **no README**, no CI, no license |
| Assignment-Data-Science- | Notebook | 17 | 2023-01-28 | **no README**, no CI, no license |
| Titanic | Notebook | 1 | 2022-11-01 | **no README**, no CI, no license |
| HimanshuPatil2001 (profile) | — | 2 | 2026-10-03 | no CI, no license |

### Findings that cut across every repo

1. **Zero CI across all 15 repos.** Nothing is verified automatically on push.
2. **Zero licenses.** A repository with no license is legally unusable by anyone else.
3. **Zero test suites.** No automated proof that anything works.
4. **Documentation is inconsistent.** Two repos already use `plan.md` / `prompt.md` /
   `done.md` — the instinct is right, but there is no shared standard.

### Findings worth acting on immediately

- **Meal_Planner commits compiled bytecode** (`__pycache__/*.pyc`). `.gitignore` is missing
  or incomplete, and these should be removed from history.
- **Three repositories have no README at all** — including one of the most substantial
  (Hotel-Review-System, 14 MB).
- **Teams-Green is the strongest architecture in the portfolio** (C#, repositories, services,
  Hangfire, Docker, SQL). It is also the closest to a production pattern and the most
  impressive to a reviewer. It deserves the best documentation.
- **Aarohi-Bot** is the second strongest (Telegram bot, Groq LLM, SQL repositories, Docker,
  memory/relationship services) and already has `Plan.md` and `done.md`.

---

## 2. Target documentation standard

Every repository that receives active work should end a cycle with this structure.

```
docs/
  00-overview.md            One-paragraph summary + status badge
  01-request/
    2026-10-03-initial.md   The original ask, in the requester's words
  02-fsd/
    functional-spec.md      Features, user stories, acceptance criteria
    out-of-scope.md          Explicitly excluded items
  03-code-plan/
    architecture.md         Component diagram, tech choices + rationale
    build-order.md          Sequenced tasks with dependencies
    risks.md                Known risks and mitigations
  04-implementation/
    changelog.md            Reverse-chronological, one entry per meaningful change
    decisions/ADR-0001-*.md One file per architectural decision
  05-testing/
    test-plan.md            What is tested, how, and what is deliberately not
  06-deployment/
    deployment.md           How to deploy; environment variables; rollback
  07-monitoring/
    runbook.md              Symptoms → diagnosis → action
  08-handover/
    handover.md             For the next maintainer
README.md                   Entry point, links into docs/
CONTRIBUTING.md             How to work in this repo
LICENSE                     MIT
```

**Not every repo needs every folder.** A 6-file script needs `00-overview.md` and a
README. A production service needs all eight. The standard scales with complexity —
the point is that the *decision* is recorded, not that every folder exists.

---

## 3. Work backlog by priority

### Priority 1 — Reputation-critical (visible to any reviewer)

| # | Repo | Work | Why it matters |
|---|---|---|---|
| 1 | Meal_Planner | Remove `.pyc`, add `.gitignore`, write README | An interviewer's first stop; currently looks unmaintained |
| 2 | All repos | Add `LICENSE` (MIT) | Free legal blocker; 1-line change each |
| 3 | Profile repo | Rebuild `README.md` as a portfolio index | The first thing anyone sees |
| 4 | Aarohi-Bot | Complete the 8-stage doc set | Strongest AI project; currently only `Plan.md` |
| 5 | Teams-Green | Complete the 8-stage doc set | Strongest architecture; already has planning docs |

### Priority 2 — Demonstrates engineering maturity

| # | Repo | Work | Why it matters |
|---|---|---|---|
| 6 | Aarohi-Bot | GitHub Actions: build on push | Proves C# project actually compiles |
| 7 | Teams-Green | GitHub Actions: build on push | Same, for the ASP.NET project |
| 8 | Meal_Planner | GitHub Actions: lint + test | Has CI already; make it meaningful |
| 9 | Teams-Green | Architecture decision records | Shows *why*, not just *what* |
| 10 | Tracking-Project | Full doc set + `requirements.txt` pinning | Computer-vision work is currently undocumented |

### Priority 3 — Depth over breadth

| # | Repo | Work |
|---|---|---|
| 11 | Teams-Green | Monitoring runbook (Hangfire, MS Graph token expiry) |
| 12 | Aarohi-Bot | Deployment + handover docs (Docker compose, SQL schema) |
| 13 | Book_reader_chatbot | Doc set; 4 MB of assets need explaining |
| 14 | Japanese-Test | Doc set for the TypeScript project |
| 15 | All notebooks | READMEs stating setup, data source, and conclusions |
| 16 | Portfolio-wide | `CONTRIBUTING.md` template |

---

## 4. Proposed daily rotation

One repo per day, cycling through Priority 1 then Priority 2. Each day produces one
**real, reviewable** change plus its documentation.

| Day | Repo | Deliverable | Doc stage |
|---|---|---|---|
| 1 | Meal_Planner | `.gitignore`, remove `.pyc` from history | 04-implementation |
| 2 | Meal_Planner | README with setup and usage | 00-overview |
| 3 | Meal_Planner | LICENSE (MIT) | 00-overview |
| 4 | Profile repo | Portfolio index README linking every repo | 00-overview |
| 5 | Aarohi-Bot | 8-stage doc skeleton, populated for existing code | 02-fsd |
| 6 | Aarohi-Bot | Architecture doc + first ADR | 03-code-plan |
| 7 | Aarohi-Bot | Build CI workflow | 05-testing |
| 8 | Aarohi-Bot | Deployment + monitoring runbook | 06/07 |
| 9 | Teams-Green | 8-stage doc skeleton | 02-fsd |
| 10 | Teams-Green | Architecture doc + ADRs | 03-code-plan |
| 11 | Teams-Green | Build CI workflow | 05-testing |
| 12 | Teams-Green | Monitoring runbook (Hangfire, Graph tokens) | 07-monitoring |
| 13 | Tracking-Project | Doc set + pinned requirements | 02-fsd |
| 14 | Tracking-Project | Architecture + per-module docs | 03-code-plan |
| 15 | Hotel-Review-System | README (14 MB repo, currently none) | 00-overview |
| 16 | Gold-Price-Forecasting | README with findings | 00-overview |
| 17 | Book_reader_chatbot | Doc set | 02-fsd |
| 18 | Japanese-Test | Doc set | 02-fsd |
| 19 | Portfolio | `CONTRIBUTING.md` + PR template | 00-overview |
| 20 | Portfolio | Release retrospective + next-cycle plan | 08-handover |

After day 20 the cycle restarts with the next-highest-value gap, chosen from a fresh audit.

### Commit message format

Not one word. Each commit names the stage it advances:

```
docs(meal-planner): add README with setup and usage (§00)
docs(aarohi): add architecture diagram and ADR-0001 (§03)
ci(aarohi): build on push with dotnet 9 (§05)
chore(meal-planner): ignore __pycache__ and drop committed .pyc (§04)
```

The **§** symbol ties every commit back to the documentation stage, so the git history
itself becomes an audit trail of the documented process.

---

## 5. What this plan deliberately does not do

- **No fake work.** Every day produces a change a reviewer would find useful.
- **No squashed mega-commits.** One meaningful change per day, as a real project would have.
- **No generated filler.** Documentation that restates the code is worse than none.
- **No secrets.** `.env.example` documents variable names and purpose only.

---

## 6. Open decisions

1. **Rotation length** — 20 days as proposed, or a shorter Priority-1-only cycle?
2. **License** — MIT across all repos?
3. **Day boundaries** — commits at 09:00 IST, so "day N" starts at 09:00 local.
4. **Scope** — document only, or document *and* fix issues found while documenting?

---

## Revision history

| Date | Change |
|---|---|
| 2026-10-03 | Initial plan drafted from full portfolio audit |
