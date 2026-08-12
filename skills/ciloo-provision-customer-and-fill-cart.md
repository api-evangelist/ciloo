---
name: Provision a Ciloo customer and fill their cart
description: Create a brand-store customer, mint their per-customer OAuth 1.0a credentials, add print items to their cart, and hand them a signed auto-login link into the Ciloo Print Platform.
api: openapi/ciloo-cart-api-openapi.yml
operations:
  - createCustomer
  - generateCustomerKeys
  - addCartItem
  - getCartItems
  - generateLoginToken
---

# Provision a Ciloo customer and fill their cart

Use this when a system of record (an intranet, a DAM, an HR tool) needs to place branded-print items
into a named person's Ciloo cart and then send them straight into the store to check out.

## Before you start

- **The base URL is the brand store, not a shared API host.** Every Ciloo brand store is its own
  hostname — `<tenant>.cilooprint.com` or a customer-owned domain — and the API lives at `/wp-json` on
  that host. Get the store domain from the customer, never assume one.
- **You need two credential tiers.** Admin credentials (`ck_admin_…` / `cs_admin_…`) come from Ciloo and
  are used *only* to mint customer keys. Cart calls use the per-customer key pair.
- **Content-Type must be `application/x-www-form-urlencoded`** on every `ciloo/v1` call. A JSON content
  type breaks the OAuth signature. (The `wc/v3` customer calls take JSON.)
- **Sign correctly or nothing works.** Base string is
  `METHOD & urlencode(url) & urlencode(sorted params)`; include the OAuth params, the path parameters,
  and — for POST and PUT only — the body parameters. Signing key is `urlencode(consumer_secret) + "&"`.
  A bad signature is the failure mode Ciloo says accounts for ~80% of integration problems.

## Steps

1. **Create the customer** — `createCustomer` (`POST /wp-json/wc/v3/customers`, JSON body with `email`,
   `first_name`, `last_name`, optional `username`, `billing`, `shipping`). Keep the returned `id`.
2. **Mint their cart credentials** — `generateCustomerKeys`
   (`POST /wp-json/ciloo/v1/generate_customer_keys`) with `customer_id` from step 1 and a
   `callback_url` you control. Ciloo POSTs the new `consumer_key`/`consumer_secret` to that URL; pass
   `return_keys=1` if you also want them in the response body. Store them server-side only — this call
   issues credentials, so gate it behind a human approval in any autonomous flow.
3. **Add each item** — `addCartItem` (`POST /wp-json/ciloo/v1/cart/add-item`), signed with the
   *customer* key. All seven fields are required: `asset_id`, `quantity`, `filename`, `productUid`,
   `pages`, `url` (a directly fetchable link to the print-ready PDF), and `item_sku`. Use your own
   stable `asset_id` — it is the handle for every later update or removal.
4. **Verify** — `getCartItems` (`GET /wp-json/ciloo/v1/cart`). The response is an object keyed by
   `asset_id`, not an array; read `cart_items[<your asset_id>]` to confirm quantity and `product_id`.
5. **Hand off the session** — `generateLoginToken` (`POST /wp-json/ciloo/v1/login-token`) with the end
   user's `ip_address`. Build `https://<store-domain>?action=autologin&token=<token>&path=/cart`. The
   token expires in one hour. `path` may be empty (portal home), `/cart`, or `/my-account/orders`.

## Rules an agent must follow

- **Nothing here is idempotent.** There is no idempotency key. Retrying `addCartItem` after a timeout
  adds the item again — re-read the cart with `getCartItems` before any retry, and reconcile on
  `asset_id`.
- **There is no rate-limit signal.** No `RateLimit-*` headers, no documented 429. Throttle yourself.
- **Read errors from the envelope, not the status code alone.** Failures come back as
  `{"success": false, "error": {"code", "message", "details", "timestamp"}, "debug": {"request_id"}}`.
  Log `debug.request_id` — it is the only correlation handle Ciloo exposes.
- **`removeCartItem` is irreversible.** Confirm with a human before deleting.
- **Never put credentials or an auto-login token in client-side code or a URL you log.** The token is a
  bearer of the customer's session.

## Related

- Conventions: `conventions/ciloo-conventions.yml`
- Errors: `errors/ciloo-problem-types.yml`
- Postman collection: `collections/ciloo-cart-api.postman_collection.json`
