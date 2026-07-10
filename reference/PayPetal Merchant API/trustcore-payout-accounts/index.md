---
title: TrustCore Payout Accounts
excerpt: >-
  Manage the bank payout accounts used for TrustCore escrow releases and
  refunds.


  **Why this is required:** before you can call `PUT
  /trustcore/{reference}/complete` or `PUT /trustcore/{reference}/refund`, the
  destination customer must have a verified bank account on file.


  **Recommended flow:**

  1. Call `GET /api/v1/account/banks` to retrieve the list of supported banks
  and their codes.

  2. Call `POST /api/v1/account/bank/validate` to resolve the account number to
  an account name — confirm this with the customer.

  3. Call `POST /api/v1/escrow/trustcore/payout/{customerId}` to link the
  validated account.
hidden: false
---