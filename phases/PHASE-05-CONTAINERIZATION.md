# Phase 05 — Containerization

**Purpose (plain English):** Package the application so it runs identically on any machine — the developer's laptop, a teammate's PC, the server. This kills the classic "it works on my machine" problem and is the foundation for automated deployment.

**Entry criteria:** Phase 04 in progress or complete (an app exists to containerize). May run in parallel with late Phase 04.

## Concepts

Dockerfile = recipe → Image = packaged app → Container = running instance.
Containers are **ephemeral**: destroyed and recreated, never repaired in place. Anything that must survive lives in a **volume**. All config enters via **environment variables**.

## Tasks

- [ ] Verify Docker (or Podman) works locally: run a stock image (e.g. `docker run hello-world`) | verify: passes: hello-world run
- [ ] Write the `Dockerfile`: official pinned base image (no `latest`), `WORKDIR`, `COPY`, `RUN`, `EXPOSE`, `CMD`; multi-stage build if it shrinks the image | verify: exists: Dockerfile; passes: docker build
- [ ] Add `.dockerignore` (node_modules/venv, .git, .env, build junk) | verify: exists: .dockerignore; contains: ".env"
- [ ] Run the container as a non-root user | verify: contains: Dockerfile "USER"
- [ ] Externalize ALL configuration to environment variables; document each in `.env.example` | verify: absent: hardcoded hosts/ports/credentials in image; .env.example complete
- [ ] Write `docker-compose.yml` (or `compose.yaml`) describing the full local stack: app + database + any other services, with named volumes for persistent data | verify: exists: compose file; passes: docker compose config
- [ ] Bring the stack up and exercise the app end-to-end inside containers | verify: passes: docker compose up + manual/scripted check
- [ ] Prove persistence: create data, destroy and recreate containers, data survives | verify: passes: recreate test, record result here
- [ ] Document container workflows in README (build, up, down, logs, exec) | verify: contains: README.md "docker compose up"

## 🔴 Gates — do not pass without

- [ ] **G5.1 One-command local run.** `docker compose up` starts the entire working stack from a clean checkout. | verify: passes on a machine/dir that never ran it before
- [ ] **G5.2 No secrets baked into images.** No credentials in Dockerfile, compose file, or image layers; secrets come from env/secret files excluded from git. | verify: absent: secrets in Dockerfile & compose; docker history spot-check
- [ ] **G5.3 Data survives container recreation.** | verify: recreate test recorded with date

## Deliverables

`Dockerfile`, `.dockerignore`, compose file, updated `.env.example`, README container docs, persistence test note.

## Owner's corner

- The magic sentence you're paying for: *"Anyone can run the whole product with one command."* Ask someone to prove it on a fresh machine.
- Ask: *"If we delete the containers, is customer data gone?"* The answer must be a confident no, with the test to prove it.
