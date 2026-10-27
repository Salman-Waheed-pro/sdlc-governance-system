# Phase 10 — Operations & Observability

**Purpose (plain English):** Keep the live product healthy and be the FIRST to know when something breaks — before users tell you. Logs, metrics, alerts, backups, and a tested way to recover. Completing this phase graduates the project to Continuous Mode.

**Entry criteria:** Phase 09 complete (production is live).

## Concepts — three pillars of observability

**Logs** (what happened), **metrics** (how much/how fast), **traces** (where time went across services). Plus **alerts** that page a human only when action is needed.

## Tasks

- [ ] Add a health endpoint (`/health` or `/healthz`) reporting app + dependency status | verify: passes: curl health endpoint returns 200 + status body
- [ ] Configure restart policies / process supervision so crashed containers restart automatically | verify: compose/orchestrator restart policy set; kill test recovers
- [ ] Implement structured logging (JSON or key-value): level, timestamp, request id; NO sensitive data (passwords, tokens, personal data) in logs | verify: log samples reviewed; absent: secrets in logs
- [ ] Centralize/retain logs so they survive container recreation and are searchable | verify: logs accessible after container restart
- [ ] Integrate error tracking (Sentry/GlitchTip or equivalent) — unhandled errors reach a dashboard with stack traces | verify: test error appears in tracker
- [ ] Collect basic metrics: request rate, error rate, latency, CPU/memory, disk | verify: metrics visible (dashboard/endpoint)
- [ ] Build a monitoring dashboard (Grafana/provider dashboard/uptime service) showing service health at a glance | verify: dashboard URL in docs/operations.md
- [ ] Define alert rules: site down, error rate spike, disk almost full — routed to a channel humans actually see | verify: alert config recorded
- [ ] **Fire drill:** deliberately break staging (or stop prod briefly in a window) and confirm the alert fires and reaches a human | verify: drill date + screenshot/note in docs/operations.md
- [ ] Schedule automated backups of all persistent data | verify: backup job exists; recent backup file present
- [ ] **Restore drill:** restore a real backup into a scratch environment and verify the data | verify: restore date + result in docs/operations.md
- [ ] Write the runbook `docs/operations.md`: how to check health, read logs, restart, roll back, restore backup, who to call | verify: exists: docs/operations.md covering all six

## 🔴 Gates — do not pass without

- [ ] **G10.1 An alert reached a human in the fire drill.** Monitoring that no one sees is decoration. | verify: drill record
- [ ] **G10.2 A backup was actually restored successfully.** An untested backup is a hope, not a backup. | verify: restore drill record
- [ ] **G10.3 The runbook exists** and a person who didn't write it can follow it. | verify: second-person walkthrough noted

## 🎓 Graduation

When all gates pass: set `mode: continuous` and all phases `complete` in `STATE.md`, write a Journal entry, and from the next session onward operate ONLY from `continuous/CONTINUOUS-MODE.md`. The phase system is finished and never runs again for this product.

## Owner's corner

- The question that matters: *"If the product went down right now, how would we find out, and how fast?"* Acceptable answer: "an alert within minutes." Unacceptable: "a customer would email us."
- Once a quarter, ask: *"When did we last restore a backup?"* Keep asking forever.
