---
title: TrustCore Escrow
excerpt: >-
  TrustCore is PayPetal's **merchant-controlled** escrow product.


  **Typical flow:**

  1. Create a customer record for both the buyer (initiator) and seller
  (counterparty).

  2. Call `POST /trustcores` to create an agreement — you receive a
  `paymentUrl`.

  3. Redirect the initiator to the payment URL to fund the escrow.

  4. PayPetal fires the `trustcore.payment.paid` webhook when the escrow is
  funded.

  5. When the transaction is complete, call `PUT
  /trustcore/{reference}/complete` to release funds to the counterparty.

  6. If the deal falls through, call `PUT /trustcore/{reference}/refund` to
  return funds to the initiator.


  Both complete and refund require the destination customer to have a bank
  payout account on file. An agreement created with a `milestone` breakdown
  instead releases funds in stages via `PUT
  /trustcore/{reference}/milestones/{milestoneId}/release`, strictly in sequence
  order.


  **Webhooks:** on each state change, PayPetal POSTs a flat JSON event to the
  webhook URL registered against your application (configured via your merchant
  dashboard, not this API). Every event includes `timestamp` and `event`, plus
  fields relevant to that event (`reference`, `transactionId`, `currency`,
  `amount`, `status`, `paymentType`, `initiator`, `counterparty`, `metadata`;
  milestone events add `milestoneId`, `milestoneDescription`, `milestoneAmount`,
  `milestoneSequence`):

  ```json

  {
    "timestamp": "2026-09-19T18:40:00Z",
    "event": "trustcore.payment.paid",
    "reference": "order-9821",
    "transactionId": "260715130001ABCBIZ1RAND",
    "currency": "NGN",
    "amount": "500000",
    "status": "ONGOING",
    "initiator": "cus_payer_id",
    "counterparty": "cus_receiver_id"
  }

  ```

  Event names: `trustcore.payment.paid`, `trustcore.payment.refund`,
  `trustcore.payment.completed`, `trustcore.milestone.released`. A delivery that
  gets no response is retried up to 3 times with exponential backoff, then
  dropped — treat webhooks as best-effort notifications and reconcile against
  `GET /trustcore?reference=...` as the source of truth. **There is currently no
  signature/HMAC verification on outbound webhooks** — don't treat an incoming
  webhook alone as sufficient authorization for a sensitive action; confirm the
  referenced agreement's state via the API first.
hidden: false
---