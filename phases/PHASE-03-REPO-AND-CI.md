# Phase 03 — Repo, Collaboration & CI Skeleton

**Purpose (plain English):** Set up the workshop before building the furniture. Version control, a branching strategy, mandatory code review, automatic code-quality checks. After this phase the team works like a professional engineering team: nobody changes the product without a second pair of eyes and a green automated check.

**Entry criteria:** Phase 02 complete.

## Choosing a branching strategy (pick ONE, record in ADR)

| Situation | Strategy |
|---|---|
| Small team / first project / default | **Feature Branch Workflow** (branch per feature → PR → merge to main) |
| SaaS deploying often | **GitHub Flow** (main always deployable) |
| Staging + production environments | **GitLab Flow** (environment branches) |
| Versioned/regulated software | **Git Flow** (develop/release/hotfix branches) |
| Mature team, heavy automation | **Trunk-Based Development** (tiny short-lived branches) |

## Tasks

- [ ] Create the repository (or verify it exists) with `README.md`, `.gitignore` for the stack, and a LICENSE decision | verify: exists: README.md, .gitignore
- [ ] Choose and document the branching strategy as an ADR | verify: exists: docs/adr/*branching*.md
- [ ] Protect the main branch: no direct pushes, PRs required, ≥1 review required, CI must pass | verify: repo settings (record screenshot/confirmation in the ADR)
- [ ] Adopt Conventional Commits (`feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `ci:`, `chore:`) — document in `CONTRIBUTING.md` | verify: exists: CONTRIBUTING.md; contains: "Conventional Commits"
- [ ] Add a PR template (description, linked issue, checklist from DoD) | verify: exists: .github/PULL_REQUEST_TEMPLATE.md or equivalent
- [ ] Write code review guidelines: reviewers check correctness, readability, security, performance, tests; PRs ≤ ~300 lines; one feature per PR | verify: contains: CONTRIBUTING.md "review"
- [ ] Configure a linter for the stack (ESLint / Ruff / Pylint / golangci-lint …) with config committed | verify: exists: lint config file; passes: lint command on skeleton
- [ ] Configure a formatter (Prettier / Black / gofmt …) — style is automated, never debated in review | verify: exists: formatter config; passes: format check
- [ ] Create the project skeleton per the architecture doc (folders matching the module boundaries, hello-world entry point, dependency manifest) | verify: skeleton builds/runs
- [ ] Create the CI skeleton (GitHub Actions or equivalent): on every push/PR → install deps → lint → format-check → (placeholder) test | verify: exists: .github/workflows/*.yml; ci: run is green
- [ ] Add `.env.example` and ensure `.env` is gitignored — config comes from environment variables from day one | verify: exists: .env.example; contains: .gitignore ".env"
- [ ] Merge the first real change through the full flow: branch → conventional commit → PR → review → green CI → merge | verify: PR history shows a reviewed, CI-passing merge

## 🔴 Gates — do not pass without

- [ ] **G3.1 Main is protected.** Direct pushes to main are impossible; PR + review + green CI are required. | verify: repo settings confirmed
- [ ] **G3.2 CI runs on every PR** and fails the PR when lint or checks fail. | verify: ci: config review + one red and one green run observed
- [ ] **G3.3 No secrets in the repo.** `.env` gitignored, no keys/passwords/tokens in history. | verify: absent: "api_key\|password=\|secret=" in tracked files; scan history if tooling available
- [ ] **G3.4 The full flow was exercised once, end to end.** | verify: link to the first merged PR recorded here

## Deliverables

Working repo with protected main, CONTRIBUTING.md, lint+format configs, CI workflow, project skeleton, first merged PR.

## Owner's corner

- From now on, **every change is a Pull Request**. If anyone says "I just pushed it directly," that's a process breach — ask why.
- Green checkmarks on PRs are your quality guarantee working automatically, 24/7, for free.
- Ask: *"Show me the last PR that failed CI and what happened next."* A healthy team has failed checks — that means the safety net works.
