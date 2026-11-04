# 03 — Database, API and event contracts (draft)

## PostgreSQL tables
- `users(id, email, password_hash, display_name, avatar_asset_id, created_at, deleted_at)`
- `couples(id, relationship_start_on, timezone, status, created_at, ended_at, version)`
- `couple_memberships(id, couple_id, user_id, joined_at, left_at)`; unique active membership per user; max two active pair members enforced transactionally.
- `couple_invites(id, couple_id, token_hash, expires_at, consumed_at, created_by)`; never store raw token.
- `milestones(id, couple_id, kind, local_date, repeat_rule, reminders_enabled)`
- `plans(id, couple_id, title, starts_at, ends_at, location_text, status, notes, version)`
- `plan_tasks(id, plan_id, title, is_done, updated_by, version)`
- `fund_goals(id, couple_id, title, target_amount_minor, currency, due_on, status)`
- `fund_entries(id, couple_id, goal_id, actor_id, entry_type, amount_minor, note, occurred_at, idempotency_key)`; derive balances from immutable entries, reversal instead of destructive edit if auditing matters.
- `media_assets(id, couple_id, uploader_id, object_key, mime, byte_size, sha256, captured_at, uploaded_at, status, visibility, deleted_at)`
- `moments(id, couple_id, created_by, caption, occurred_at, created_at)` / `moment_media(moment_id, asset_id, sort_index)`
- `recap_preferences(couple_id, daily_enabled, weekly_enabled, local_trigger_time, template_id, min_photos)`
- `recap_jobs(id, couple_id, period_type, period_start_utc, period_end_utc, status, media_snapshot_json, attempts, output_asset_id, created_at)`; unique idempotency key.
- `device_tokens(user_id, platform, token_ciphertext, last_seen_at)`
- `notification_preferences(user_id, type, enabled)`
- `outbox_events(id, aggregate_type, aggregate_id, couple_id, event_type, payload_json, published_at)`

Use UUID or ULID consistently, `TIMESTAMPTZ` instants, `DATE` for anniversary calendar dates; integer money in minor currency units (e.g. VND denomination, document rounding). Check constraints, FK, indices on `(couple_id, occurred_at)`, and partial unique indices where required. Keep actual migration SQL reviewed by agent.

## Public REST surface (draft)
- `POST /api/v1/auth/register`, `POST /login`, `/refresh`, `/logout`, `DELETE /me`
- `POST /api/v1/couples/invites`, `POST /api/v1/couples/join`, `GET /api/v1/couples/me`, `PATCH /api/v1/couples/me`
- `GET /api/v1/milestones/upcoming`, `POST /api/v1/milestones`
- `GET /api/v1/plans`, `POST /api/v1/plans`, `PATCH /api/v1/plans/{id}`, `DELETE /api/v1/plans/{id}`
- `GET /api/v1/funds/goals`, `POST /api/v1/funds/goals`, `POST /api/v1/funds/entries`
- `POST /api/v1/media/upload-intents`, `POST /api/v1/media/{id}/complete`, `GET /api/v1/media/{id}/download-url`
- `GET /api/v1/moments?cursor=...`, `POST /api/v1/moments`, `DELETE /api/v1/moments/{id}`
- `GET /api/v1/recaps`, `POST /api/v1/recaps`, `GET /api/v1/recaps/{id}`, `POST /api/v1/recaps/{id}/regenerate`
- `PUT /api/v1/me/notifications/preferences`, `POST /api/v1/me/devices`

## Realtime strategy
- REST is source of truth; websocket transports metadata change notifications, not photo bytes.
- Example envelope:
  ```json
  {"id":"event-uuid","type":"MOMENT_CREATED","coupleId":"uuid","resourceId":"uuid","occurredAt":"ISO-8601","version":1}
  ```
- Subscriptions authorized pair-scoped, enforced server-side on every subscription and mutation.
- On reconnect, fetch `GET /api/v1/moments?cursor=...`; never assume a WebSocket event is durable delivery.
- Avoid duplicate event application with event ID and entity version; push notification is a hint only.

## Priority test cases
- Pair invite consumed by two concurrent users -> only one success and never >2 members.
- User A cannot fetch B's pair media by guessing UUID, changing coupleId, or websocket subscription.
- Pair member removed -> all future REST and websocket access denied; signed URL expiry limits old links.
- Upload intent size mismatch, invalid MIME, expired signature, cancelled upload -> deny/cleanup.
- Recap schedule across timezone/daylight changes and photo timestamps; no duplicate jobs on retries.
- Fund concurrent writes and duplicate client retry -> no double-count.
- Video worker crash -> job retry and no leaked temporary files.
