---
name: Chargeback Crown Clef policy
description: Product rule for reversing purchased voting currency after payment disputes.
---

When a Shopify chargeback is confirmed, purchased Crown Clefs credited by the disputed order must be revoked. The adjustment must be recorded in the wallet ledger and must not silently alter votes already cast.

**Why:** Crown Clefs represent paid value, so a successful chargeback cannot leave the disputed purchase spendable while preserving a clean payment-to-wallet audit trail.

**How to apply:** Match the chargeback to the original Shopify order, reverse only the remaining unspent Crown Clefs from that order, and flag accounts where some or all of the Clefs were already used for manual review or a defined debt/freeze flow. Implement this with an idempotent Shopify chargeback/refund event handler; do not rely on a one-time manual subtraction.