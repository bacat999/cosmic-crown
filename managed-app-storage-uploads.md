---
name: Managed App Storage uploads
description: Durable security and URL conventions for owner-managed media uploaded directly to Replit App Storage.
---

Use short-lived sidecar-signed URLs for direct browser uploads, but treat those upload keys as temporary. Finalization must copy verified bytes to a distinct server-only published key, re-verify that copy, and persist only its stable application URL.

**Why:** Signed PUT metadata is controlled by the uploader and does not prove the bytes are a supported image or playable video. Even after verification, the original PUT URL remains reusable until it expires, so serving that same key creates an overwrite race. Stable application URLs also prevent expiring storage signatures from leaking into database records.

**How to apply:** For new managed media kinds, issue a temporary upload through the existing registry. Before any GET, require HEAD size to equal the bounded declaration; enforce the same byte limit while streaming. Validate format, publish to a new server-only key, re-verify that copy, and only then persist its internal URL. A still-valid old PUT must never affect published bytes.

Deletion is durable lifecycle state, not a best-effort side effect. Keep each temporary or unpublished object registered until App Storage DELETE succeeds or returns 404, and register destination keys before copying bytes. Protect long verification with a renewable lease whose duration exceeds every bounded storage operation.

**Why:** Deleting a registry row before deleting its object creates an untraceable storage orphan if the process crashes or storage is temporarily unavailable. Reclaiming by creation age alone can also delete bytes underneath a verifier that is still active.

**How to apply:** Mark failed, superseded, and temporary objects as pending deletion; claim cleanup work atomically; delete the object first; then remove the matching claimed row. Retry expired cleanup claims, exclude verified rows, and only reclaim verification work after its lease expires.