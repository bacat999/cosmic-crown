---
name: Video artifact registration
description: A workflow constraint for keeping delegated video artifacts registered and routed correctly.
---

Preserve the artifact tool’s managed manifest when delegating or iterating on video artifacts. Do not let a generated legacy manifest replace it.

**Why:** A legacy-style video manifest can leave the code intact while removing the managed workflow and making preview resolution fall through to the root app.

**How to apply:** After delegated video work, confirm the artifact still has a kind, title, preview path, and managed web workflow before adding audio or presenting it. If registration was replaced, restore it through the artifact tools while preserving the finished media files.