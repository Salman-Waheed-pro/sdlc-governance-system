# Incident Response

**When production is broken or degraded, this file outranks everything else.**

## During the incident — in order

1. **Declare it.** Post in the team channel: what's broken, who's responding (that person is now Incident Lead), when it started. One thread = the incident log.
2. **Stabilize first, diagnose later.** The fastest fix is usually **rollback to the previous tagged version** (rehearsed in Phases 07/09 — steps in `docs/operations.md`). Roll back FIRST if in doubt; root-cause on your own time, not the users'.
3. **Communicate.** If users are affected > 15 min, post a status note (status page / social / email). Honest and boring beats silent.
4. **Timestamp everything** in the thread: what you observed, what you tried, what changed. This becomes the postmortem timeline.
5. **Confirm recovery** with the same signal that detected the failure (alert cleared, smoke test green, error rate normal). Announce resolution.

## Hard rules

- 🔴 No debugging live on production by editing files on the server. Fix via the pipeline (rollback or hotfix PR — the per-change loop applies even at 2am; a second person reviews, even briefly).
- 🔴 Never blame a person, during or after. Systems fail; people respond.
- If customer data may have been exposed: owner is informed immediately; legal notification duties (e.g. GDPR 72h) are checked before anything is deleted.

## After the incident — blameless postmortem (within 5 working days)

Use the template in `templates/TEMPLATES.md`. File as `docs/postmortems/YYYY-MM-DD-short-name.md`:

- Timeline (from the thread)
- Impact: who/what/how long
- Root cause — keep asking "why" past the first answer (the Team Nova lesson: the outage wasn't the missing database index, it was that no one could see production)
- What went well / what went poorly in the response
- **Action items with owners and board cards** — a postmortem without cards changed nothing

The agent verifies within a week that every postmortem action item exists on the board.
