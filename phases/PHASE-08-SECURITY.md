# Phase 08 — Security Hardening (DevSecOps)

**Purpose (plain English):** Security is not a final inspection — it's built into the pipeline so problems are caught the moment they appear ("shift left"). This phase wires automated security checks in and fixes what they find, BEFORE the product faces the public internet.

**Entry criteria:** Phase 07 complete. **Production launch is forbidden until this phase's gates pass.**

## Tasks

- [ ] Enable dependency vulnerability scanning (Dependabot / `npm audit` / `pip-audit` / Renovate) with alerts on and auto-PRs where available | verify: scanning enabled; config or platform setting recorded
- [ ] Add secrets scanning to CI (gitleaks / trufflehog / GitHub secret scanning) and scan the FULL git history once | verify: ci: secrets scan step; history scan result recorded
- [ ] Add static analysis security testing (SAST — CodeQL / Semgrep / Bandit) to CI | verify: ci: SAST step; run green or findings triaged
- [ ] Scan the Docker image (Trivy / Grype / Docker Scout) in CI; fail on critical vulnerabilities | verify: ci: image scan step with severity threshold
- [ ] Review authentication & authorization against the threat model: password hashing (bcrypt/argon2), session/token expiry, every endpoint checks permissions | verify: code review notes in docs/security-review.md
- [ ] Validate ALL external input (API payloads, forms, query params) server-side | verify: validation layer exists; spot-check endpoints
- [ ] Enforce HTTPS everywhere; set security headers (CSP, HSTS, X-Content-Type-Options) at the edge/app | verify: staging response headers checked
- [ ] Lock down infrastructure: firewall/security groups minimal, no database exposed to the internet, SSH by key only | verify: docs/security-review.md infra section
- [ ] Apply least privilege to ALL credentials: CI tokens, DB users, cloud roles — each can do only what it needs | verify: credentials inventory in docs/security-review.md
- [ ] Triage every finding: fix criticals/highs now; record accepted risks with owner sign-off | verify: docs/security-review.md findings table complete
- [ ] Check data-protection duties (GDPR etc. if handling personal data): what's collected, why, how deleted on request | verify: contains: docs/security-review.md "Data protection"

## 🔴 Gates — do not pass without

- [ ] **G8.1 Zero unaddressed critical/high vulnerabilities** in dependencies, code, and container image. "Addressed" = fixed, or risk-accepted in writing by the owner. | verify: scanner outputs + findings table
- [ ] **G8.2 Full-history secrets scan is clean** (or leaked secrets were rotated and the rotation recorded). | verify: scan result + rotations noted
- [ ] **G8.3 Security checks run automatically in CI** on every PR from now on — this phase installs a permanent guard, not a one-time audit. | verify: workflow contains dep+SAST+image+secret scan steps
- [ ] **G8.4 Auth review done:** hashing, session expiry, per-endpoint authorization confirmed. | verify: docs/security-review.md signed by reviewer

## Deliverables

Security scanning wired into CI, `docs/security-review.md` (findings, fixes, accepted risks, credentials inventory, data-protection note).

## Owner's corner

- This is the phase that protects you from the news headline. Do not let anyone compress it.
- Ask: *"Show me the current list of security findings and which are still open."* An honest team always has a list; "no findings ever" means nobody looked.
- You personally sign off any "accepted risk." If you don't understand a risk, it isn't accepted yet.
