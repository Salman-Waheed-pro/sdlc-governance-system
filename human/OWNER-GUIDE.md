# Owner's Guide — Managing a Tech Team Without Being Technical

You don't need to understand code to run this project well. You need to understand **the process**, ask **the right questions**, and refuse to skip **the gates**. This guide gives you all three.

## How this system works (2 minutes)

The project moves through 11 phases (`phases/` folder). Each phase has tasks, deliverables, and **🔴 gates** — the critical checks that must never be skipped. Your team or AI agent works the checklists; completed items get ~~struck through~~ with evidence. `STATE.md` always shows where the project is. When all phases finish, the project switches permanently to **Continuous Mode** (`continuous/CONTINUOUS-MODE.md`) — lighter recurring loops instead of phases.

**Your job:** read the Journal in `STATE.md` weekly, attend one 30-minute review, ask the questions below, and personally sign the things marked for you. You are the only person allowed to approve skipping a task — and nobody, including you, can skip a gate.

## The phases in plain English + your one killer question for each

| # | Phase | Means | Your question |
|---|---|---|---|
| 00 | Inception | Agree why/who/how before building | "What does 'done' mean here?" |
| 01 | Planning | Slice the idea into a small first version | "Which single assumption does the MVP test?" |
| 02 | Architecture | Decide how it's built; write decisions down | "What's our monthly cost at launch and at 10× users?" |
| 03 | Repo & CI | Set up review + automatic quality checks | "Show me the last change that failed a check." |
| 04 | Development | Build the MVP in small reviewed steps | "Can I see a demo — today?" |
| 05 | Containers | Package so it runs anywhere with one command | "If we delete the containers, is data gone?" |
| 06 | Testing | Build the safety net | "If the core feature broke tonight, what catches it?" |
| 07 | CI/CD | Automate the road to the server | "When did we last practice rollback?" |
| 08 | Security | Wire security scans into the pipeline | "Show me the open security findings list." |
| 09 | Release | Version, changelog, launch checklist, go live | "Walk me through the signed launch checklist." |
| 10 | Operations | Know before users when something breaks | "How would we find out the site is down, and how fast?" |

## Universal red flags 🚩

- **"Trust me, it's done"** — done means struck through in the phase file WITH evidence. Ask to see the file.
- **"We'll add tests/security later"** — later never comes; that's what gates are for. Gates cannot be skipped, even by you.
- **"It's 80% done"** for two weeks — ask for a demo, not a percentage.
- **A quiet board** — if the Kanban board doesn't match what people say they're doing, the board is lying or the people are.
- **Hero fixes** — someone fixing production directly on the server "just this once." That's how outages are born (read the Team Nova story below).
- **No bad news** — healthy projects surface problems weekly. Zero problems reported = problems hidden.

## Your recurring rituals

- **Weekly (30 min):** read the `STATE.md` Journal → look at the board → look at the dashboard (post-launch) → see a demo if anything shipped → reorder priorities.
- **Per release:** read the changelog; click the product yourself like a stranger would.
- **Monthly (post-launch):** ask "when did we last restore a backup?" and "what did the retro decide to try?"
- **Per incident:** expect a blameless postmortem within 5 days, with action items on the board. Never ask "whose fault?" — ask "what guardrail was missing?"

## Why this matters — the Team Nova story (60 seconds)

A team built a great dashboard. Deployments were manual, monthly, and walled off from developers. Launch day: the site melted for three days; rollback took a week; root cause took a month. The cause? One missing database index — trivial to fix, invisible because developers couldn't see production and operations didn't know the app. The cost wasn't the bug; it was **silos and missing process**. Every gate in this system exists to prevent a Team Nova moment: reviews catch the index before launch, staging catches it before users, monitoring catches it in minutes not days, rollback rehearsals turn a week into five minutes.

## Words you'll hear, decoded

**PR (pull request)** = a proposed change waiting for review · **CI** = robots checking every change automatically · **Staging** = the dress-rehearsal copy of the product · **Rollback** = instantly returning to the previous version · **MVP** = smallest useful first version · **ADR** = a written-down decision with its reasons · **SemVer** = version numbers with meaning (2.3.1: big.new.fix) · **Changelog** = human-readable list of what changed · **Feature flag** = a switch to turn a feature on/off without redeploying · **Postmortem** = blameless incident report · **Coverage** = % of code exercised by tests
