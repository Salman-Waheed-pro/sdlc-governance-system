# Project State

> Single source of truth. The agent updates this file; humans read it.
> Do not edit by hand unless correcting an error — the agent trusts this file.

```yaml
project: "<PROJECT NAME HERE>"
mode: lifecycle          # lifecycle | continuous
current_phase: 0         # 0-10 while mode: lifecycle
last_audit: never        # ISO date of last full verification pass
last_updated: never
updated_by: none         # agent/human who last wrote this file
```

## Phase register

| Phase | Name | Status | Gates passed | Completed on |
|---|---|---|---|---|
| 00 | Inception & Team | pending | 0/3 | — |
| 01 | Product Planning | pending | 0/3 | — |
| 02 | Architecture & Design | pending | 0/4 | — |
| 03 | Repo, Collaboration & CI Skeleton | pending | 0/4 | — |
| 04 | Development | pending | 0/3 | — |
| 05 | Containerization | pending | 0/3 | — |
| 06 | Testing & QA | pending | 0/3 | — |
| 07 | CI/CD Pipeline | pending | 0/3 | — |
| 08 | Security Hardening (DevSecOps) | pending | 0/4 | — |
| 09 | Release & Production Readiness | pending | 0/3 | — |
| 10 | Operations & Observability | pending | 0/3 | — |

Statuses: `pending` → `in-progress` → `complete` (only after all gates verified) | `blocked`

## Journal

> Append-only log. One line per session: date — phase — what was done — by whom.

- (empty)
