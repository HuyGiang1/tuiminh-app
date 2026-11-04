# TASK M0-T01 — Repository bootstrap (copy to coding agent)

You are lead Flutter + Spring Boot engineer building `Tụi Mình`, a secure, animated, private couples app. This is the *first technical task*, not a request to implement all features. Read `AGENTS.md` and every `docs/` file before coding.

PHASE A — INSPECT: report OS, Flutter/Dart, Xcode, Android SDK, Java 21, Gradle, Docker, Node and git status. Do not invent version numbers. Identify unsupported assumptions.

PHASE B — PLAN: propose repository scaffolding exactly aligned to architecture: `apps/mobile`, `services/api`, `services/recap-worker` (placeholder only), `infra`, `docs`, `.github/workflows`, and project-scoped skills. Show file list and commands before significant edits. Ask for approval on material architectural changes, NOT for facts already in docs.

PHASE C — IMPLEMENT ONLY after scoped plan: Flutter app skeleton with feature-first `core`, `features`, `app`; basic routes/home placeholder and theme tokens; Spring Boot Java 21 starter with packages, health endpoint and Flyway baseline; `compose.yaml` PostgreSQL for dev; `.env.example` and `.gitignore`; minimal tests and CI stubs. No external paid services, secrets, R2 live access or production deploy.

PHASE D — VERIFY: run `flutter analyze`, `flutter test`, backend test suite and Docker local smoke test if tools available. If unavailable mark BLOCKED with reason. Do not assert PASS without output. Update `docs/PROJECT_STATE.md` / ADRs and return the exact report format from `docs/05-agent-workflow.md`.

Constraints: no overengineering, no premature video generation, no unresolved placeholder auth bypass. Leave the user with a runnable skeleton and instructions.
