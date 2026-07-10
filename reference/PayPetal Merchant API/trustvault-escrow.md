---
title: TrustVault Escrow
excerpt: >-
  TrustVault is a **customer-controlled** escrow product. Unlike TrustCore, the
  merchant does not trigger the release — the customer does.


  **Typical flow:**

  1. Call `POST /agreement` to create an agreement — you receive a hosted
  payment URL.

  2. Redirect the customer to the payment URL to fund the escrow.

  3. When the customer is satisfied and ready to release funds, call `PUT
  /agreement/auth/{reference}` to send them a one-time code by email.

  4. The customer supplies the code to `PUT /agreement/complete/{reference}` to
  release the funds to the merchant.


  This flow is suited for situations where the buyer controls the release —
  freelance work, service delivery, peer-to-peer sales.
hidden: false
---