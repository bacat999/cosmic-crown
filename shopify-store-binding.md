---
name: Shopify store binding
description: How to avoid reading or configuring the wrong Shopify store for T.A.S.K. 888.
---

Treat `ontask888.shop` (store name **We OnTask888**) as the confirmed customer-facing Shopify storefront. The former `ontask888.myshopify.com` hostname returns Shopify 404s and is not a valid checkout authority. Before using the Replit Shopify connector for catalog or admin work, query `shop.myshopifyDomain` and confirm with the merchant that it is the permanent Shopify domain behind `ontask888.shop`.

**Why:** A Replit-provisioned connection remained bound to a separate sandbox store while `ontask888.shop` served the real password-protected **We OnTask888** storefront. Treating that connector as authoritative could mutate the wrong store or replace valid live-store mappings with invented data.

**How to apply:** Public checkout links may use `ontask888.shop`. For catalog reads, product changes, or webhook configuration, stop if the connector still reports the sandbox domain; rebind it to the merchant store first. Never infer variant IDs from Shopify's numeric sequence.

Keep the approved launch checkout lightweight: purchases begin from buttons inside T.A.S.K. 888, then continue through Shopify-hosted checkout. Do not add an embedded cart, custom payment fields, or extra Storefront API traffic unless the merchant later requests that expansion.

**Why:** The merchant explicitly chose the simplest low-usage flow, leaving payment security and checkout operations with Shopify while the app only attributes the order and processes the signed paid-order webhook.

For music, keep Shopify Digital Downloads as the source for tracks customers purchase and download, and keep audition/voting playback copies in T.A.S.K. App Storage. A track that is both sold and voted on intentionally has one file for each purpose, linked by its Shopify product/variant ID. Google Drive and Google Sheets are not required for the live workflow.

**Why:** Shopify should own customer delivery and purchase records, while T.A.S.K. needs dependable playback and artist/vote metadata without exposing paid master files or creating a second spreadsheet-based source of truth.