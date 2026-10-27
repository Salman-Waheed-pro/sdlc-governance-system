# Phase 00 — Inception & Team

**Purpose (plain English):** Before anything is built, agree on WHY the project exists, WHO is doing it, and HOW you will work together. Most failed projects fail here — silently — by skipping this.

**Entry criteria:** none (first phase).

## Tasks

- [ ] Write the project charter from `templates/TEMPLATES.md` → save as `docs/charter.md` (problem, goal, scope, out-of-scope, stakeholders, success criteria, constraints) | verify: exists: docs/charter.md; contains: docs/charter.md "Out of scope"
- [ ] List the team roster with roles — humans AND AI agents count; assign who owns product decisions, who owns technical decisions | verify: contains: docs/charter.md "Roster" or exists: docs/team.md
- [ ] Each member writes a "My User Manual" (how I work, when I'm available, how to give me feedback) — for solo/AI-run projects, document the owner's availability and decision turnaround time | verify: exists: docs/team/*.md or section in docs/team.md
- [ ] Write Ways of Working (WoW): meeting/check-in cadence, communication channels, decision-making rule, conflict resolution | verify: exists: docs/ways-of-working.md
- [ ] Write the Definition of Done (DoD) — the checklist every piece of work must pass before it counts as finished (reviewed, tested, documented, deployed to staging…) | verify: exists: docs/definition-of-done.md
- [ ] Establish the communication channel(s) and record where they are (Slack/Teams/Discord/email thread) | verify: contains: docs/ways-of-working.md "channel"
- [ ] Identify stakeholders and user groups; note how each will be consulted | verify: contains: docs/charter.md "Stakeholders"

## 🔴 Gates — do not pass without

- [ ] **G0.1 Charter approved.** The product owner has read the charter and their approval is recorded (name + date) in `docs/charter.md`. | verify: human: owner; contains: docs/charter.md "Approved by"
- [ ] **G0.2 Success is measurable.** The charter states at least 2 concrete success criteria a non-technical person could check (e.g. "a user can order and pay in under 3 minutes"), not vibes ("app is good"). | verify: contains: docs/charter.md "Success criteria" with measurable statements
- [ ] **G0.3 DoD exists and includes review + testing.** Definition of Done explicitly requires code review and automated tests. | verify: contains: docs/definition-of-done.md "review"; contains: docs/definition-of-done.md "test"

## Deliverables

`docs/charter.md`, `docs/ways-of-working.md`, `docs/definition-of-done.md`, team roster.

## Owner's corner (non-technical)

- Read the charter yourself. If you can't explain the project's goal in one sentence after reading it, send it back.
- The "Out of scope" list protects your budget. If it's empty, that's a red flag.
- Ask: *"What does 'done' mean on this project?"* — the answer should match `definition-of-done.md`.
