# Phase 06 — Testing & QA

**Purpose (plain English):** Build the safety net. Automated tests find failures before users do and make every future change safe. Motto: *"If it's not tested, it's broken — you just don't know it yet."*

**Entry criteria:** Phase 04 substantially done (there is logic to test). Ideally tests were written alongside code; this phase makes the strategy complete and enforced.

## Strategy — the testing pyramid

Many fast **unit tests** (single functions/classes, Arrange–Act–Assert, deterministic) → fewer **integration tests** (components together: service + real database, preferably in containers) → few **end-to-end tests** (whole user journeys). Mock external paid/slow services (payments, email) — but don't mock so much the tests prove nothing.

## Tasks

- [ ] Choose and configure the test runner(s) for the stack; `npm test`/`pytest`/equivalent runs the whole suite with one command | verify: passes: single test command
- [ ] Unit tests for core business logic — every module from `docs/architecture.md` has tests for its public interface | verify: test files exist per module; passes: suite
- [ ] Integration tests for the critical paths (API + database at minimum), using containerized dependencies where possible | verify: integration tests exist and pass
- [ ] API tests: every endpoint tested for success case, validation failure, and auth failure | verify: coverage of route list
- [ ] Frontend component tests for key user interactions (if the product has a UI) — test behavior, not implementation details | verify: exist and pass, or N/A recorded with reason
- [ ] At least one end-to-end test covering the single most important user journey (the MVP assumption from Phase 01) | verify: e2e test exists and passes
- [ ] Set a coverage threshold with the owner and tech lead (recommended start: 70% on core logic) and enforce it in the test config | verify: coverage report ≥ threshold; threshold in config
- [ ] Wire tests into CI: every PR runs the suite; failures block merge | verify: ci: workflow runs tests; a failing test demonstrably blocks a PR
- [ ] Write the test plan + how-to-run docs (`docs/testing.md`): what's covered, what's deliberately not, how to run each layer | verify: exists: docs/testing.md

## 🔴 Gates — do not pass without

- [ ] **G6.1 CI blocks merges on test failure.** Demonstrated once with a deliberately broken test. | verify: PR blocked-by-red-tests recorded here with link/date
- [ ] **G6.2 The money path is tested end-to-end.** The core user journey (signup→core action→result, or whatever the MVP promises) has an automated test. | verify: named e2e test exists
- [ ] **G6.3 Coverage meets the agreed threshold** and the threshold is enforced automatically, not by promise. | verify: coverage gate in CI/test config

## Deliverables

Test suite (unit/integration/API/e2e), coverage report, `docs/testing.md`, tests enforced in CI.

## Owner's corner

- Tests are the reason changes next year will be cheap instead of terrifying. This phase is an investment, not overhead.
- Ask: *"If the payment/core feature silently broke tonight, what would catch it?"* The answer should be a test name, not a person's name.
- Ask to see the coverage number monthly. Falling coverage = the team is borrowing from the future.
