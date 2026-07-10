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
  payout account on file.
hidden: false
---