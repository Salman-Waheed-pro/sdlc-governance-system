# Phase 09 — Release & Production Readiness

**Purpose (plain English):** Turn "the code works on staging" into "version 1.0.0 is live for real users" — with proper version numbers, human-readable release notes, and a launch checklist that catches the boring mistakes that break launches.

**Entry criteria:** Phase 08 complete (security gates passed).

## Concepts

- **Semantic Versioning (SemVer):** `MAJOR.MINOR.PATCH` — breaking change / new feature / bug fix. Conventional Commits (Phase 03) can compute this automatically.
- **Feature flags:** deploy code OFF, switch it on gradually. Deployment ≠ release.
- **Environments:** development → staging → production, each with its own config and secrets, production the most restricted.

## Tasks

- [ ] Adopt SemVer; create the first annotated release tag (e.g. `v1.0.0`) | verify: annotated tag exists; `git tag -n` shows message
- [ ] Create `CHANGELOG.md` (generated from conventional commits or hand-written), entries per version, newest first | verify: exists: CHANGELOG.md with v1.0.0 section
- [ ] Make tags trigger the release pipeline (tag → build → publish image `v1.0.0` → deploy) | verify: ci: tag trigger configured; observed run
- [ ] Add a feature-flag mechanism for risky features (env-var flags are enough to start) | verify: at least the mechanism exists and is documented
- [ ] Provision production environment: separate host/project, separate secrets, pinned image versions (never `latest`) | verify: docs/environments.md production section; compose/manifests pin versions
- [ ] Complete the Production Readiness Checklist from `templates/TEMPLATES.md` (domain, TLS, DNS, backups scheduled, error pages, legal/privacy pages, support contact) | verify: exists: docs/release-checklist-v1.md fully checked
- [ ] Deploy to production with manual approval gate; run smoke tests against production | verify: production URL live; smoke results recorded
- [ ] Announce the release: notes published (GitHub Release / notes page) readable by non-developers | verify: release notes published
- [ ] Rehearse production rollback once (to previous tag) | verify: date + duration recorded in docs/release-checklist-v1.md

## 🔴 Gates — do not pass without

- [ ] **G9.1 Owner signed the Production Readiness Checklist.** Every line checked or consciously waived in writing. | verify: human: owner signature line in docs/release-checklist-v1.md
- [ ] **G9.2 Production runs a pinned, tagged version** that exactly matches a tested image — no `latest`, no hand-patched files on the server. | verify: running image tag == git tag
- [ ] **G9.3 Production rollback rehearsed.** | verify: recorded rehearsal

## Deliverables

`v1.0.0` tag, `CHANGELOG.md`, release pipeline, production environment live, signed `docs/release-checklist-v1.md`, published release notes.

## Owner's corner

- The version number + changelog is how you, support, and customers talk about the product. Ask for the changelog with every release, forever.
- Before signing the checklist: click the production site yourself, on your phone, as a stranger would. You will find something.
- Ask: *"If this release goes wrong at 2am, what exactly happens?"* — expected answer: rollback to the previous version in minutes, then investigate in the morning.
