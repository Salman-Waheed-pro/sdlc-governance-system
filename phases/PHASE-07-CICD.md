# Phase 07 — CI/CD Pipeline

**Purpose (plain English):** Automate the road from "code merged" to "running on a server." Humans stop copying files to servers; the pipeline builds, tests, packages, and deploys the same way every time. Fewer errors, faster releases, smaller risks.

**Entry criteria:** Phases 05 & 06 complete (containerized app + enforced tests).

## Target pipeline

```
Push/PR → Lint → Unit tests → Integration tests → Build → Docker image
        → Push image to registry (tagged) → Deploy to STAGING → Smoke tests
        → [manual approval] → Deploy to PRODUCTION   (production leg activates in Phase 09)
```

## Tasks

- [ ] Extend CI to build the Docker image on every merge to main | verify: ci: workflow builds image; run green
- [ ] Push images to a registry (GHCR/Docker Hub/cloud registry) tagged with git SHA + branch — never only `latest` | verify: registry shows SHA-tagged images
- [ ] Store ALL pipeline credentials in the CI secret store (GitHub Actions secrets or equivalent) — zero secrets in workflow files | verify: absent: secrets in .github/workflows/**; secrets configured in platform
- [ ] Provision a staging environment (VM/container host/PaaS) that mirrors production shape | verify: staging URL/host recorded in docs/environments.md
- [ ] Automate deploy to staging on merge to main (SSH+compose pull, or platform deploy) | verify: merge → staging updates without human steps
- [ ] Add post-deploy smoke tests: hit the health endpoint + one core flow; failure marks the deploy red | verify: ci: smoke step exists; observed run
- [ ] Write and TEST the rollback procedure: redeploy previous image tag in ≤ 5 minutes | verify: rollback rehearsed once; steps + date in docs/environments.md
- [ ] Use caching (deps, docker layers) to keep pipeline under ~10 minutes | verify: recent run duration
- [ ] Document the pipeline in `docs/pipeline.md`: stages, triggers, secrets used (names only), how to re-run, how to roll back | verify: exists: docs/pipeline.md

## 🔴 Gates — do not pass without

- [ ] **G7.1 Merge-to-main deploys to staging automatically**, end to end, with no manual file copying. | verify: observed run linked here
- [ ] **G7.2 Rollback was actually rehearsed** — not just documented. | verify: rehearsal date + who + duration recorded
- [ ] **G7.3 No credentials in the repo or workflow files**; all in the secret store. | verify: scan of workflows + repo

## Deliverables

Full CI/CD workflow files, image registry with tagged images, live staging env, smoke tests, tested rollback, `docs/pipeline.md`, `docs/environments.md`.

## Owner's corner

- After this phase, "deploying" stops being an event and becomes a non-event. That's the goal.
- Ask: *"How long from a bug fix being approved to it being on staging?"* Healthy answer: minutes, automatically.
- Ask: *"When did we last practice rollback?"* — practiced, not written. An untested rollback plan is a wish.
