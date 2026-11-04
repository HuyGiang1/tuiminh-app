# Tụi Mình — Couple App Starter Kit

> Planning and agent handoff kit, **not a running app**. Working title only. Version: 2026-11-04.

## Stack decision
- Client: Flutter / Dart, feature-first MVVM (Riverpod + go_router + Dio).
- Backend: Spring Boot / Java 21, modular monolith, PostgreSQL, Flyway, Spring Security.
- Realtime: authenticated WebSocket event stream + REST source of truth; FCM for offline push.
- Media: private Cloudflare R2 with short-lived signed upload/download URLs, server-side metadata.
- Video: async isolated FFmpeg worker, not an abandoned FFmpegKit mobile dependency.
- Design: Figma editable design system, Rive for mascots, Lottie for simple decorative motion.

## Start here
1. Create a private Git repository; copy this kit to the repository root.
2. Read `docs/00-product-brief.md`, `docs/01-architecture.md`, `docs/02-design-system.md`.
3. On Mac, install Flutter, Xcode (for iOS), Android SDK, JDK 21, Docker, Node.js.
4. Use **OpenAI Codex** with the official **Dart and Flutter** plugin. Follow the [official Flutter setup guide](https://docs.flutter.dev/ai/get-started) for Codex:
   ```bash
   codex plugin marketplace add flutter/agent-plugins
   codex plugin add dart-flutter@dart-flutter
   codex plugin list
   ```
   The plugin supplies Dart/Flutter skills and MCP configuration. Plugin installation alone does not verify SDK readiness or a running app connection.
5. Optionally add `frontend-design` for visual design guidance:
   ```bash
   npx skills add anthropics/skills --skill frontend-design --agent universal --yes
   ```
   Review downloaded skill contents before allowing scripts. This skill is primarily web-oriented; the project's Flutter mobile design system takes precedence. A local copy already exists in `.agents/skills/frontend-design/`; no reinstall is needed when present.
6. Keep the four project-specific skills in `.agents/skills/`:

   | Skill | Purpose |
   |---|---|
   | `couple-design-review` | Mobile screens, mascots, motion, design tokens and accessibility, including reduced motion. |
   | `couple-spring-security` | Spring Boot authentication, pairing, pair-scoped REST/WebSocket authorization, migrations and concurrency tests. |
   | `couple-media-recap` | Private R2 photo uploads, metadata, cleanup and asynchronous recap video jobs/workers. |
   | `couple-release-qa` | Evidence-based QA and milestone review, test/security checks and project handoff. |

7. Start Codex from the repository root, where `AGENTS.md`, `docs/` and `.agents/skills/` are located:
   ```bash
   cd /path/to/tuiminh-app
   codex
   ```
8. Verify skill discovery before requesting implementation. In Codex CLI, run `/skills` or type `$` to view available skills. Confirm all four `couple-*` skills, the Dart/Flutter plugin skills, and `frontend-design` if installed. Codex discovers repository skills from `.agents/skills/<skill-name>/SKILL.md`; see [Codex skill discovery](https://developers.openai.com/codex/skills). Restart Codex if a skill is missing after installation. Ask:
   ```text
   Read-only inspection only. Read AGENTS.md, list the discovered local and
   plugin skills and available Dart/Flutter MCP tools, and report anything
   missing or unavailable. Do not modify files, install packages or access cloud services.
   ```
   A skill listed in the filesystem is not proof that Codex discovered it, and a discovered skill is not proof that its MCP tools are available. Runtime inspection and hot reload require a connected running app.
9. Paste `prompts/01-bootstrap.md` into Codex when ready to begin. **Planning, docs and scaffolding only**: do not deploy or open production accounts.
10. After every task, Codex updates `docs/PROJECT_STATE.md` + `docs/DECISIONS.md` as required by `AGENTS.md` and reports tests/commit, unless the task explicitly restricts edits to other files.

## ChatGPT handoff
Create a ChatGPT Project called `Tụi Mình – Product & Engineering`. Upload product, architecture, design, decisions and current state docs; add project instructions from `prompts/05-chatgpt-project-instructions.md`. To resume, share the latest commit and `docs/PROJECT_STATE.md` with ChatGPT. Repository state is authoritative, memory is supplementary.

## Index
- [Product brief](docs/00-product-brief.md)
- [Architecture](docs/01-architecture.md)
- [Design system](docs/02-design-system.md)
- [Data/API contract](docs/03-api-data-contract.md)
- [Delivery milestones](docs/04-roadmap.md)
- [Agent operating agreement](docs/05-agent-workflow.md)
- [Project state](docs/PROJECT_STATE.md)
- [Architectural decisions](docs/DECISIONS.md)
- [Prompts](prompts/)
- [Custom project skills](.agents/skills/)
