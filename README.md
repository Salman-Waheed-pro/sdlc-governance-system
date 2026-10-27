# SDLC Governance System

A file-based operating system for software projects. Drop this folder into any repository and it turns any coding agent (Claude Code, Codex, Gemini CLI, Amp, Cursor, Roo Code…) — or any human team — into a governed delivery machine that follows the full software lifecycle, phase by phase, and refuses to skip the critical checks.

## What it does

- **Guides**: 11 phases from project inception to production operations, each with tasks, deliverables, and hard gates.
- **Verifies**: the agent doesn't just tick boxes — every deliverable has a verification rule (a file that must exist, a command that must pass, a pattern that must NOT be found). The agent scours the actual project for evidence before marking anything done.
- **Records**: completed tasks are checked off and struck through with a date and evidence pointer, so the files themselves are the audit trail.
- **Graduates**: when all 11 phases pass their gates, the project switches to **Continuous Mode** — a different, lighter system of recurring loops (per-change, per-release, weekly, monthly, per-incident). The phase system never runs again.
- **Translates**: `human/OWNER-GUIDE.md` lets a non-technical product owner supervise the whole thing — what each phase means, what to ask, and the red flags that mean something is wrong.

## Files

| File | Who reads it | Purpose |
|---|---|---|
| `GOVERNANCE.md` | The AI agent / tech lead | The boot protocol: how to find the current phase, verify, work, and record |
| `STATE.md` | Agent + humans | Single source of truth for current phase and mode |
| `phases/PHASE-00 … PHASE-10` | Agent + team | The lifecycle checklists with gates and verification rules |
| `continuous/CONTINUOUS-MODE.md` | Agent + team | The post-launch operating system (replaces the phases) |
| `continuous/INCIDENT-RESPONSE.md` | Everyone | What to do when production breaks |
| `human/OWNER-GUIDE.md` | Non-technical owner | Plain-English supervision manual |
| `human/dashboard.html` | Non-technical owner | Open in any browser — visual phase/gate tracker |
| `templates/TEMPLATES.md` | Team | Charter, ADR, DoD, test plan, postmortem, release checklist… |

## How to install on a project

1. Copy this whole folder into the project repository root (keep the folder name, e.g. `governance/`).
2. Fill in the project name in `STATE.md`.
3. Tell your coding agent: **"Read governance/GOVERNANCE.md and follow it."** Add that line to the project's `CLAUDE.md` / `AGENTS.md` so every session boots into it automatically.
4. The owner opens `human/dashboard.html` and reads `human/OWNER-GUIDE.md`.

## The one rule

**No phase is complete until its 🔴 gates are verified with evidence.** Gates are the "critical things you must not let go without a look." Everything else is negotiable; gates are not.


## Related

[govern-plugin](https://github.com/Salman-Waheed-pro/govern-plugin) packages this system as a Claude Code plugin with `/govern` and a read-only `/inspect` security and completeness auditor.

## License

MIT
