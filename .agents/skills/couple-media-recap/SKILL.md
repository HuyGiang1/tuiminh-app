---
name: couple-media-recap
description: Use when implementing private R2 uploads, photo metadata, WebSocket events, image cleanup and video generation.
---

# Implement photo upload and safe recap video pipeline

Keep bucket private. Use signed PUT/GET URLs with short expiry, validate size/mime/hash and HEAD on completion, quota enforcement and orphan cleanup. No passive photo import. Strip GPS EXIF by default. Store event metadata, not photo bytes, in realtime messages. Build async idempotent recap jobs and a worker with CPU/time/temp-storage limits; use only licensed or original audio; never synchronously encode in API. Test negative auth, retries, cancellation and removal.
