# Architecture decision log

## ADR-001 (PROPOSED): Flutter for both platforms
Reason: one codebase for iPhone/Samsung, rich custom animations. Tradeoff: platform-native bridges for advanced media.

## ADR-002 (PROPOSED): Spring Boot modular monolith
Reason: shared business data and secure relationship isolation, without premature microservices.

## ADR-003 (PROPOSED): Private R2 signed URLs
Reason: object storage, client-direct upload, no public couples gallery. Tradeoff: explicit auth, quotas, cleanup and signed-link expiry.

## ADR-004 (PROPOSED): Asynchronous independent video worker
Reason: heavy encoding must not tie up API server. Avoid retired mobile FFmpegKit. Worker consumes idempotent job records.

## ADR-005 (PROPOSED): Figma + Rive as design sources
Reason: visually editable UI and character state-machine animations; implemented as Flutter native widgets.

## ADR-006 (PROPOSED): Not a bank
Fund is a shared expense and savings ledger only, no custodial money movement or direct payment in MVP.

> Owner must mark approved/changed and add dated ADRs for deviations. Never silently edit prior decisions.
