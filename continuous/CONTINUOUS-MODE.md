# Continuous Mode — Post-Launch Operating System

**This file replaces the phase system.** It activates when `STATE.md` says `mode: continuous`.
There are no phases anymore. There are **loops** — recurring checklists at five cadences. The agent's boot sequence in continuous mode:

1. Read `STATE.md` Journal → what happened last session.
2. Check the **per-change loop** compliance of anything merged since last session.
3. Run whichever scheduled loops are due (weekly/monthly) — see "Loop log" below.
4. Work the board (top of Ready column) inside the per-change loop.
5. Append a plain-English Journal line to `STATE.md`.

The 🔴 rules below are permanent gates — they inherit their authority from GOVERNANCE.md and may never be skipped.

---

## Loop 1 — Per change (every piece of work)

- [ ] Work item exists on the board with acceptance criteria before code starts
- [ ] Feature branch → conventional commits → PR ≤ ~300 lines
- [ ] 🔴 Review + green CI (lint, tests, security scans) before merge — no exceptions, including "tiny" changes and hotfixes
- [ ] Docs updated in the same PR if behavior changed
- [ ] Auto-deploy to staging + smoke test passed
- [ ] Card moved to Done only when the Definition of Done is met

## Loop 2 — Per release

- [ ] Version bumped per SemVer (breaking/feature/fix)
- [ ] `CHANGELOG.md` updated; release notes readable by non-developers
- [ ] Annotated git tag pushed; pipeline publishes the pinned image
- [ ] 🔴 Production deploy only from a tagged, staging-tested image, with approval
- [ ] Post-deploy smoke test on production; watch error dashboard for 30 minutes
- [ ] Risky features behind flags; gradual rollout when possible

## Loop 3 — Weekly (owner + team, ~30 min)

- [ ] Review the board: anything In Progress > 5 days? Ask why, split or unblock
- [ ] Review dashboard: error rate, latency, uptime vs last week
- [ ] Review open security alerts (Dependabot etc.) — criticals fixed within the week
- [ ] Demo anything shipped
- [ ] Owner reorders backlog priorities

## Loop 4 — Monthly

- [ ] Retrospective (blameless): keep / stop / try — record in `docs/retros/`
- [ ] Dependency updates batch-merged; coverage number checked vs threshold
- [ ] 🔴 Backup restore drill (restore into scratch env, verify data) — record date
- [ ] Cost review: infra spend vs the Phase 02 budget; investigate creep
- [ ] DORA-style health check: deploy frequency, lead time, failure rate, time-to-recover — trending better or worse?
- [ ] Prune: dead code, unused deps, stale flags, stale docs

## Loop 5 — Per incident

→ Follow `continuous/INCIDENT-RESPONSE.md`. Every production incident MUST end with a blameless postmortem filed in `docs/postmortems/`.

---

## When to reopen the phase system

Never, for this product. But START A NEW `STATE.md` (fresh lifecycle, usually fast-forwarding phases 0–3) when:
- building a **new product**, or
- a change is so large it invalidates the architecture (new platform, rewrite, major compliance regime) — treat it as a project inside the project: mini-charter, ADRs, then back into continuous mode.

## Loop log

> The agent records the last run date of each scheduled loop here.

| Loop | Last run | By | Notes |
|---|---|---|---|
| Weekly | — | — | — |
| Monthly | — | — | — |
| Restore drill | — | — | — |
