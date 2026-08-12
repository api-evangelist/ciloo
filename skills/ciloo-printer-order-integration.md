---
name: Integrate a production partner with Ciloo order callbacks
description: Receive print orders from Ciloo on your own endpoint and post production-status and shipping callbacks back to Ciloo's inbound callback URL.
api: asyncapi/ciloo-printer-webhooks.yml
operations:
  - order.create
  - order.status
  - order.shipped
---

# Integrate a production partner with Ciloo order callbacks

This is the printer side of Ciloo's on-demand production model: Ciloo pushes an order to *your* system,
and you push status back to *Ciloo's* system. Neither side polls.

## Before you start

- **Agree an authentication method with Ciloo first.** Ciloo publishes no fixed scheme for this
  integration — the page says validation is printer-dependent and asks you to contact
  `support@ciloo.com` to choose one. Do not assume a shared secret or an HMAC signature exists; there is
  no published signing or replay-protection scheme on these callbacks, so treat the inbound order
  endpoint as internet-exposed and validate at your own perimeter (mutual TLS, IP allow-list, or a
  bearer token you agree with Ciloo).
- **Publish one order endpoint** that accepts `POST` with a JSON body — e.g.
  `https://yourprinter.com/api/orders/create`.
- **Receive one callback URL from Ciloo** — e.g.
  `https://dashboard.cilooprint.com/ciloo-order-callback/printer-inbound`.

## Steps

1. **Accept the order (`order.create`, Ciloo → you).** The body is `{"orderData": {…}}` carrying
   `sourceOrderId` (Ciloo's id, e.g. `Ciloo-1054`), `customerName`, `items[]` and `shipments[]`. Each
   item carries `sourceItemId`, `quantity`, `productionSKU`, `productionCost`, `mockup_url` and
   `components[]`; each component carries `code` (e.g. `text|cover`), `path` (the artwork PDF) and
   `attributes` (`pageSize`, `substrate`, `ColorType`, `orientation`). Each shipment carries `shipTo`
   and `carrier{code, service}`.
2. **Answer immediately with your own identifiers** — `{"_id": "<your order id>", "timestamp":
   "<ISO 8601>"}`. Ciloo echoes your `_id` back as `OrderId` on every later callback, so it must be
   stable.
3. **Validate before you accept.** Fetch every `components[].path` and confirm the artwork is reachable
   and matches the declared `pageSize`/`substrate`. Reject with a non-2xx status rather than accepting
   an order you cannot produce.
4. **Post production milestones (`order.status`, you → Ciloo).** `POST` to the Ciloo callback URL with
   `TimeStamp`, `OrderId` (yours), `SourceOrderId` (Ciloo's) and `OrderStatus`. Give Ciloo your list of
   supported status values up front — the integration deliberately does not fix an enumeration.
5. **Post shipping (`order.shipped`, you → Ciloo).** Same endpoint, richer body: add `ShipmentIndex`
   (0-based, increment per shipment), `TrackingNumber`, `TrackingUrl`, `CarrierMethod` (`tracked`),
   `CarrierCode`, `CarrierService`, `sourceItemIds[]` (which Ciloo items are in this box) and the full
   `shipTo` block.

## Rules an agent must follow

- **Always send both identifiers.** `SourceOrderId` is how Ciloo finds the order; `OrderId` is how you
  find it. A callback missing either cannot be reconciled.
- **Partial shipments are the normal case.** Split by `sourceItemIds` and increment `ShipmentIndex`;
  never re-send index 0 for a second box.
- **No delivery guarantee is published.** Ciloo documents no retry or acknowledgement policy for these
  callbacks, so keep an outbox with your own retry and mark a callback delivered only on a 2xx.
- **Never invent an `OrderStatus`.** Use only values you and Ciloo have agreed.

## Related

- Webhook catalog with the verbatim payloads: `asyncapi/ciloo-printer-webhooks.yml`
- Provider documentation: https://api.cilooprint.com/printer-api-integration/
