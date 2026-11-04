# 00 — Product brief

## Product vision
A private, playful digital home for exactly two people. Design should feel warm and whimsical while everyday tasks remain fast and understandable. Working name: **Tụi Mình / Our Little World**. The app is not a public social network.

## Roles & onboarding
- User may sign up solo, create an invite code/deep link, and explicitly confirm pairing.
- One user belongs to at most one ACTIVE pair at a time in MVP; exactly two members per active pair.
- Both partners have equal authority over jointly owned content. Financial entries retain actor/creator for audit.
- Leaving/unpairing revokes access to new pair resources. Define and implement export, retention and deletion flows before launch.
- Date of relationship and timezone configurable with both partners informed.

## P0 must-have features
| Feature | User story | Acceptance |
|---|---|---|
| Pairing | Invite partner | One-time expiring code, auth required, cannot join own pair, safe concurrency |
| Love counter | Show days together | Calendar-day count in couple timezone; both see same count |
| Anniversary | Upcoming milestones | 30/100/365 days, monthly/yearly and custom dates, opt-in notifications |
| Home | Immersive love landing | Mascot hero with day count, next event, today's moment, short quick actions |
| Memories | Shared photo timeline | Explicit select→upload→verify; chronological by captured_at, secure download |
| Plans | Dates & tasks | Joint CRUD, participant notifications, conflict-safe edits |
| Finance | Savings target, ledger | Contributions/expense entries and totals; no actual payment or bank custody |
| Daily/weekly recap | Revisit photos | Deterministic selection, photo recap preview and queued generated video |
| Privacy | Couple-only access | No public gallery, secure URL expiry, report/data export/delete controls |

## P1 differentiators
- Personalized two-character Rive mascot animation with tap interactions and themed celebrations.
- Private love notes / scheduled letters (opt-in, spoiler-safe notifications).
- Date idea prompts, wish list, map venue links, mood stickers (not invasive tracking).
- Shared home widgets for iOS/Android, optional theme packs.
- Video album editing (sequence, captions, templates, copyright-safe licensed soundtrack).

## Explicit non-goals (MVP)
- Bank integration, holding funds, payment settlement, financial advice.
- Live video call, continuous GPS tracking, passive monitoring of the other partner.
- Public follower feeds or stranger discovery.
- Automatic importing of entire camera rolls, scraping private photos.
- AI emotional profiling or sentiment scoring of the relationship.

## Product rules to confirm during design
1. Date count: day 1 on anniversary start date (user-facing), calendar timezone fixed per pair.
2. For empty/no photos period: show cozy recap card, **do not** render a meaningless blank video.
3. Video render requires at least 3 eligible photos by default, user opt-out and permission to exclude any photo.
4. Daily default 21:00 Asia/Ho_Chi_Minh, weekly Sunday 21:00; configurable and disabled by default until opted in.
5. Original photos, thumbnails, recaps have independent retention and deletion policies.
6. Pair financial ledger is only a tracking tool, not proof of real cash balance.

## UX success benchmarks (targets, not claims)
- Home fully usable in <= 2 taps for primary actions.
- Normal 2–5 MB photo upload shows progress, retry and recoverable error.
- Realtime update reaches online partner quickly and resync repairs missed events.
- Both users can recognize privacy controls and unlink/delete consequences.
