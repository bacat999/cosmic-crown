---
name: Stripe and Shopify payment boundary
description: The planned separation between T.A.S.K. 888 app payments, Stripe onboarding, and the Shopify storefront.
---

Treat Stripe and Shopify as separate payment surfaces. Stripe onboarding is intended for the T.A.S.K. 888 app’s digital products or services, while the Shopify account and its custom store domain remain the authority for physical merchandise, inventory, shipping, and Shopify-hosted checkout.

The published app domain is `ontask888.app`; the customer-facing Shopify store domain is `ontask888.shop`. Neither domain replaces the other, and Stripe does not host or own the Shopify store domain.

**Why:** The merchant has both an existing Stripe account that is still in onboarding and a purchased Shopify store domain. Mixing the domains or describing Shopify merchandise as app-native Stripe products could make payment onboarding and customer routing unclear.

**How to apply:** When preparing Stripe onboarding copy, clearly describe the app’s actual digital offerings (for example, virtual voting/support products) and separately identify physical merchandise as sold through Shopify. Before changing checkout code, confirm which product categories belong in Stripe versus Shopify.