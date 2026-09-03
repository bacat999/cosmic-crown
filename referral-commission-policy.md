---
name: Referral commission policy
description: Durable attribution, tier, and ledger rules for the T.A.S.K. 888 referral program.
---

Every registered account receives a stable referral code. Attribution is first-touch, self-referrals never earn commission, and commission applies only to eligible Crown Pack and Voting Pass merchandise revenue—not shipping or tax.

Commission begins at 15%. Reaching $1,000 in cumulative eligible referral sales permanently unlocks 20% for future eligible orders; the order that crosses the threshold still uses the rate active before that order.

Commission records begin as pending. Shopify's signed paid-order webhook is the authority that creates the auditable, idempotent ledger record; browser attribution alone never creates earnings.

**Why:** This keeps earnings resistant to client tampering and webhook retries while preserving a clear, permanent incentive tier.

**How to apply:** Any new checkout path must carry the account and referral attribution into Shopify, and any new eligible product must be included in the server-side signed-order calculation before it can earn commission.