# 04 — Milestone roadmap with gates

## M0 — Discovery and baseline
Decide MVP and what is deliberately omitted; UX sitemap and privacy plan; initial ADRs. Gate: product brief and 5 core flow descriptions reviewed.

## M1 — Brand & design prototype
Figma design tokens, mascot direction, 5 navigation page high-fidelity views, click-through prototype, empty/loading/error states. Gate: user approves visual direction using screenshots; accessibility check.

## M2 — Repo bootstrap / engineering hygiene
Flutter skeleton, Spring Boot Java 21 skeleton, PostgreSQL Docker Compose, Flyway, shared API schema, CI quality checks, `.env.example`, GitHub branch strategy. Gate: fresh clone + documented local launch succeeds, test job green.

## M3 — Account and pairing
Registration/login/refresh, invites, join, relationship date/timezone, paired homepage counter. Gate: true two-device test iPhone ↔ Android; security and concurrency tests.

## M4 — Moments pipeline
Explicit photo picker, signed R2 PUT/GET, post-upload HEAD verification, secure timeline, cached preview, WebSocket update, push. Gate: offline/retry, unauthorized access and cleanup tests.

## M5 — Calendar, date plans and anniversary
Create/edit joint plans, events, custom milestones, scheduled push preference, upcoming countdown. Gate: timezone/date and concurrency tests.

## M6 — Shared fund
Savings goals, ledger contributions/expenses, balances and progress, actor trace. Gate: duplicate retries and concurrent entries remain correct.

## M7 — Video recap v1
Photo selection snapshot, daily/weekly opt-in schedule, job status, async worker + MP4 output, retries, preview and deletion. Gate: output video validates on iOS/Android, job dedup, cost limits, user consent.

## M8 — Delight + polish
Interactive Rive mascots, celebration scenes, haptics, low-motion alternatives, localization, performance and visual regression screenshots. Gate: no animation jank on representative low/mid devices.

## M9 — Privacy, beta, production
Data export/delete and unpair; backup+restore drill; penetration/security review; monitoring/cost alerts; app store privacy disclosures; TestFlight/closed beta. Gate: no known release blockers, tested incident recovery.

## Prioritization note
Do not start complex video before secure photo upload and pairing work. Video is a differentiator, but privacy and reliability determine whether people will trust the app.

## Definition of done for each task
- Acceptance cases checked; scoped files and architecture preserved.
- Backend test and Flutter analyze/test (as relevant) executed; results shown, no false PASS.
- No secrets; migrations reversible/reviewed; API docs updated.
- UX screenshots provided for UI changes; reduced-motion path checked.
- Commit hash, decisions and PROJECT_STATE written.
