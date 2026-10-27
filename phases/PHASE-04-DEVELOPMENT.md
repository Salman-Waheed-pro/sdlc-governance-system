# Phase 04 — Development

**Purpose (plain English):** Build the MVP — in small, reviewed, tracked increments. This phase overlaps with Testing (05–06 practices apply as they come online); it is complete when every MVP story meets the Definition of Done.

**Entry criteria:** Phase 03 complete. Work only on stories from the board (Phase 01).

## Standing rules while developing

- Every change: board card → feature branch → conventional commits → PR ≤ ~300 lines → review → green CI → merge.
- Code follows the module boundaries from `docs/architecture.md`. Crossing a boundary requires an ADR update, not a shortcut.
- Configuration (URLs, ports, credentials) comes from environment variables — never hardcoded.
- Documentation is updated in the same PR that changes behavior (README setup steps, API docs).
- WIP limit respected: finish and merge before starting the next story.

## Tasks

- [ ] Implement MVP stories one by one; move cards across the board as they progress | verify: board reflects reality; merged PRs link to stories
- [ ] Keep `README.md` runnable: a new developer (or agent) can set up and run the project from README alone | verify: passes: fresh setup following only README
- [ ] Maintain a dependency policy: add only justified dependencies; record heavyweight additions in an ADR; keep lockfile committed | verify: exists: lockfile; no unexplained deps
- [ ] Write/update inline docs for public interfaces of each module | verify: spot-check module entry points
- [ ] Hold a short retrospective at the midpoint of the MVP: what's slow, what's confusing, one improvement adopted | verify: exists: docs/retros/*.md ≥ 1
- [ ] Demo working software to the owner at least once mid-phase (screen recording counts) | verify: human: owner confirms seeing a demo; note date here
- [ ] All MVP stories meet the Definition of Done | verify: cross-check docs/definition-of-done.md against each story

## 🔴 Gates — do not pass without

- [ ] **G4.1 Every merge went through a reviewed, CI-green PR.** No direct commits to main since Phase 03. | verify: git log of main shows only merge/PR commits
- [ ] **G4.2 No secrets or hardcoded config in code.** | verify: absent: "password\|api[_-]?key\|secret" as literals in src/**; .env still gitignored
- [ ] **G4.3 The MVP runs end-to-end from a clean checkout** following README instructions only. | verify: passes: clean-checkout run

## Deliverables

Working MVP (all MVP stories done per DoD), current README, ≥1 retro note, demo shown to owner.

## Owner's corner

- Ask for a demo **every week or two**. "It's 80% done" without a demo means nothing; working software is the only honest progress report.
- Look at the board: cards stuck "In Progress" for more than a few days are where problems hide. Ask about the oldest card, not the newest.
- If the team says "we'll clean it up later," ask them to show you the board card for that cleanup. No card = it won't happen.
