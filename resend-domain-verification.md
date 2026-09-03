---
name: Resend domain verification
description: Resend connector behavior when a domain is verified in the dashboard but rejected by app sends
---

The Replit Resend connection uses a send-only credential and cannot manage or inspect domains. A domain shown as verified in a Resend browser workspace may still be rejected by the app if the connection belongs to another Resend workspace or uses a stale credential.

**Why:** An app send can return “domain is not verified” even when the same domain is green in the dashboard; the send-only connector has no domain-management endpoint available for reconciliation.

**How to apply:** Keep Google Workspace MX records unchanged, do not enable Resend Receiving when Google handles inbound mail, and align the Replit Resend connection with the Resend workspace that owns the verified sending domain before retrying delivery.