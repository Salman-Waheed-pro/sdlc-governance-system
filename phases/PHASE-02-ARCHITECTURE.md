# Phase 02 — Architecture & Design

**Purpose (plain English):** Decide HOW the product will be built before writing real code: what technologies, what pieces, how they talk to each other, and how the product will stay secure, fast, cheap, and easy to change. Decisions are written down so they can be questioned later.

**Entry criteria:** Phase 01 complete.

## Tasks

- [ ] Choose the tech stack (language, framework, database, hosting) and record WHY in an ADR | verify: exists: docs/adr/0001*.md
- [ ] Write the architecture document `docs/architecture.md`: components, responsibilities, data flow diagram (text/ASCII/mermaid is fine) | verify: exists: docs/architecture.md; contains a diagram
- [ ] Define module boundaries: each module's single responsibility and its public interface — this is what makes the product **modular** | verify: contains: docs/architecture.md "Modules" with ≥2 modules and stated interfaces
- [ ] Design the data model (entities, key fields, relationships) | verify: contains: docs/architecture.md "Data model" or exists: docs/data-model.md
- [ ] Record an ADR for every significant choice (database, auth approach, hosting, framework) using `templates/TEMPLATES.md` → Architecture Decision Record | verify: exists: docs/adr/*.md ≥ 3
- [ ] Write a lightweight threat model: what data is sensitive, who might attack, top 5 risks and their mitigations (STRIDE-lite) | verify: exists: docs/threat-model.md
- [ ] Set resource-efficiency budgets: expected users at launch, response-time target, monthly infra cost ceiling | verify: contains: docs/architecture.md "Budgets" with a cost number and a latency number
- [ ] State the scalability plan: what breaks first at 10x users, and the pre-planned response | verify: contains: docs/architecture.md "Scalability"

## 🔴 Gates — do not pass without

- [ ] **G2.1 Decisions are recorded, not tribal.** ≥ 3 ADRs exist; each states context, decision, and consequences. | verify: exists: docs/adr/*.md; each has "Consequences"
- [ ] **G2.2 Security was considered before code.** Threat model exists and names the sensitive data and how it's protected (encryption, auth, access). | verify: exists: docs/threat-model.md; contains: "sensitive"
- [ ] **G2.3 Cost has a ceiling.** A monthly infra cost budget is written down and the stack choice respects it. | verify: contains: docs/architecture.md cost figure
- [ ] **G2.4 Modularity is explicit.** Module boundaries and interfaces are documented — "we'll figure it out in code" fails this gate. | verify: Modules section review

## Deliverables

`docs/architecture.md`, `docs/adr/*.md` (≥3), `docs/threat-model.md`, budgets.

## Owner's corner

- ADRs are your protection against "we've always done it this way." Any tech choice without an ADR can be challenged.
- Ask: *"What's our monthly hosting cost at launch, and at 10x users?"* No answer = fail gate G2.3.
- Ask: *"What's the most sensitive data we hold, and where is it protected?"* — the answer should match the threat model.
- You don't need to understand the diagram; you need to see that it exists and the team can walk you through it in 5 minutes.
