# Templates

Copy the relevant block into `docs/` and fill it in. Keep templates boring; the value is in the answers.

---

## Project Charter → `docs/charter.md`

```markdown
# Project Charter — <name>
**Date:** | **Owner (product decisions):** | **Tech lead (technical decisions):**

## Problem
What hurts, for whom, today? (2-4 sentences, no tech words)
## Goal
One sentence. If you need two, the project isn't defined yet.
## Success criteria
- [ ] Measurable outcome 1 (a non-technical person can check it)
- [ ] Measurable outcome 2
## Scope — we WILL
- ...
## Out of scope — we will NOT (yet)
- ...
## Stakeholders
| Who | Interest | How consulted |
## Roster
| Name (human/AI) | Role | Owns |
## Constraints
Budget: € /month infra | Deadline: | Compliance:
## Approved by
<owner name>, <date>
```

## Ways of Working → `docs/ways-of-working.md`

```markdown
# Ways of Working
- Check-in cadence: (e.g. async daily note + weekly 30-min owner review)
- Channel(s): <where>
- Decisions: product = owner decides; technical = tech lead decides; both recorded (ADR for tech)
- Feedback: direct, kind, about the work
- When stuck > 1 hour: ask in channel, don't sink time silently
- Response-time expectation: <e.g. same working day>
```

## Definition of Done → `docs/definition-of-done.md`

```markdown
# Definition of Done — a work item is DONE only when:
- [ ] Acceptance criteria met
- [ ] Code reviewed by someone who didn't write it
- [ ] Automated tests added/updated and green
- [ ] Lint & format checks pass
- [ ] No new security warnings
- [ ] Docs updated (README/API) if behavior changed
- [ ] Deployed to staging and smoke-checked
- [ ] Board card closed with a link to the PR
```

## My User Manual → `docs/team/<name>.md`

```markdown
# My User Manual — <name>
Role: | Best hours: | Contact:
I work best when: | I struggle when:
Give me feedback by: | You can count on me for:
```

## Architecture Decision Record → `docs/adr/NNNN-title.md`

```markdown
# ADR NNNN: <decision title>
**Date:** | **Status:** proposed / accepted / superseded by NNNN
## Context
The forces at play: requirements, constraints, options considered.
## Decision
We will <decision>, because <reasons>.
## Consequences
Good: ... | Bad/accepted trade-offs: ... | Revisit when: ...
```

## User Story (backlog entry)

```markdown
### <ID>. As a <user>, I want <goal> so that <benefit>
Priority: | MVP: yes/no | Estimate: S/M/L
Acceptance criteria:
- [ ] ...
```

## Test Plan → `docs/testing.md`

```markdown
# Test Plan & Report
## Strategy
Pyramid: unit (target %), integration (critical paths), e2e (core journey)
## How to run
Unit: `<cmd>` | Integration: `<cmd>` | E2E: `<cmd>` | Coverage: `<cmd>`
## Deliberately not tested (and why)
## Known issues / bug tracking
Bugs live on the board with label `bug`; severity: blocker/major/minor.
## Latest report
Date: | Suite result: | Coverage: %
```

## Production Readiness Checklist → `docs/release-checklist-vX.md`

```markdown
# Production Readiness — vX.Y.Z
- [ ] All Phase 08 security gates still green (rescan run this week)
- [ ] Domain + DNS + TLS certificate valid (auto-renewing)
- [ ] Production secrets set, distinct from staging, stored in secret store
- [ ] Image version pinned to the release tag
- [ ] Backups scheduled AND a restore has been tested
- [ ] Health endpoint + alerting live
- [ ] Error pages (404/500) are humane; support contact visible
- [ ] Privacy policy / terms published (if personal data)
- [ ] Load sanity check done (expected launch traffic ×3)
- [ ] Rollback rehearsed for this release path
- [ ] Changelog + release notes written
**Owner sign-off:** <name>, <date> — waived items & reasons: ...
```

## Blameless Postmortem → `docs/postmortems/YYYY-MM-DD-name.md`

```markdown
# Postmortem: <title>
**Date:** | **Duration:** | **Severity:** | **Lead:**
## Impact
Who/what was affected, how long, how many users.
## Timeline
- HH:MM event...
## Root cause
Keep asking why. The person is never the root cause; the missing guardrail is.
## What went well / poorly
## Action items
| Action | Owner | Board card | Due |
```

## Retrospective → `docs/retros/YYYY-MM-DD.md`

```markdown
# Retro — <date>
Keep: | Stop: | Try (max 2, with owners):
Follow-up on last retro's "Try": done? effect?
```

## Peer / User Acceptance Feedback → `docs/feedback/YYYY-MM-DD-<who>.md`

```markdown
# Feedback session — <tester> on <date>
Setup: tester used <env> with <instructions given>
| # | What happened | Expected | Severity | Board card |
Top 3 impressions in tester's own words:
```
