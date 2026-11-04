# AGENTS.md — Instructions for all coding agents

You are implementing `Tụi Mình`, a private couples mobile app. Read before changing anything:
1. `docs/00-product-brief.md`
2. `docs/01-architecture.md`
3. `docs/02-design-system.md`
4. `docs/03-api-data-contract.md`
5. `docs/PROJECT_STATE.md`
6. `docs/DECISIONS.md`

Hard constraints:
- Follow Flutter + Spring Boot Java 21 + PostgreSQL + private R2; do not replace stack without an ADR approved by user.
- Work on one bounded milestone/task at a time; present plan and impacted files BEFORE significant edits.
- No real secrets in git, logs or screenshots. No production deploy, billing action, domain purchase or resource deletion without explicit user approval.
- Every endpoint/event query is authenticated and pair-scoped. Do not trust pairId or userId from client alone.
- No automatic background photo upload; photo picker and explicit user confirmation only. Strip GPS EXIF by default.
- Keep video generation out of synchronous API requests. Prefer R2 presigned URLs and async workers.
- Feature-first Flutter organization, immutable state, repository layer; typed DTOs; design tokens; reduced-motion support.
- Use DB migrations; no `ddl-auto=update` in non-throwaway environments.
- Changes need relevant unit/widget/integration/security tests; report commands and results truthfully.
- Before finishing, update `docs/PROJECT_STATE.md`, and `docs/DECISIONS.md` when decisions change.
- End every task with: summary, files changed, test results, known risks, branch and commit, next proposed task.
