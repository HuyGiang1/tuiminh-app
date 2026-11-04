---
name: couple-spring-security
description: Use when implementing APIs, database migrations, pairing, permissions, WebSockets or concurrent writes.
---

# Secure Spring Boot pair-scoped features

Read `docs/01-architecture.md` and `docs/03-api-data-contract.md`. Define threats and acceptance tests first. Authenticate each operation; derive pair membership server-side; use Spring Security on REST and WebSocket CONNECT/SUBSCRIBE; never trust client pairId. Use Flyway, constraints, transactions, idempotency, access denial integration tests and concurrency tests. Show exact test output.
