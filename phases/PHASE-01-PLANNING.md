# Phase 01 — Product Planning

**Purpose (plain English):** Decide WHAT to build first. Turn the goal into user stories, cut them down to a Minimum Viable Product (MVP), and set up a visible board so anyone can see what's happening at any time.

**Entry criteria:** Phase 00 complete (all gates verified).

## Concepts the team must apply (not just read)

- **Agile values:** working software over documentation; responding to change over following a plan.
- **Kanban:** visualize all work; limit work-in-progress (WIP); finish before starting.
- **MVP:** the smallest product that delivers real value and tests the core assumption. Learn before expanding.
- **User story format:** *As a `<user>`, I want `<goal>` so that `<benefit>`* — plus acceptance criteria.

## Tasks

- [ ] Write user stories covering the product vision (aim 8–20) in `docs/backlog.md` or the issue tracker | verify: exists: docs/backlog.md or ≥8 issues in tracker
- [ ] Give every story acceptance criteria (bullet list of checkable conditions) | verify: each story has ≥1 acceptance criterion
- [ ] Define the MVP: mark the 3–7 stories that form it, and write one sentence stating the assumption the MVP tests | verify: contains: docs/backlog.md "MVP"; MVP story count ≤ 7
- [ ] Prioritize the rest of the backlog (ordered list, not buckets) | verify: backlog is an ordered list
- [ ] Create the Kanban board (GitHub Projects or equivalent) with columns: Backlog / Ready / In Progress / In Review / Done — and a WIP limit on In Progress | verify: board exists; record its URL in docs/backlog.md
- [ ] Sketch a rough roadmap: MVP → next 2 increments (dates optional, order mandatory) | verify: contains: docs/backlog.md "Roadmap"
- [ ] Owner reviews and reorders priorities | verify: human: owner sign-off line in docs/backlog.md

## 🔴 Gates — do not pass without

- [ ] **G1.1 MVP is genuinely minimal.** ≤ 7 stories, and the team can state in one sentence what assumption it tests. If the MVP takes more than ~4–6 weeks to build, it is not an MVP — cut it. | verify: MVP section review
- [ ] **G1.2 Every MVP story has acceptance criteria** a non-developer could check. | verify: manual scan of MVP stories
- [ ] **G1.3 Work is visible.** The board exists, its URL is recorded, and every current task is on it. Untracked side-work is forbidden from here on. | verify: contains: docs/backlog.md board URL

## Deliverables

`docs/backlog.md` (stories + MVP + roadmap), live Kanban board.

## Owner's corner

- You should be able to open the board and understand project status **without asking anyone**. If you can't, the board is wrong, not you.
- Push back on MVP size. The most common failure is an MVP that is secretly the whole product.
- Ask: *"Which single assumption does this MVP test?"* One clear answer = healthy. A list = scope creep.
