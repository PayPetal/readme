---
title: Bank & Account Tools
excerpt: >-
  List supported Nigerian financial institutions, validate a bank account
  number, and manage subwallets for the authenticated merchant.


  **How to use these endpoints:**

  1. Call `GET /banks` to get the list of supported banks and their `code`
  values. Cache this — it changes rarely and every other endpoint that takes a
  `bankCode` expects a value from here.

  2. Before saving any bank account anywhere (e.g. as a TrustCore payout
  destination), call `POST /bank/validate` with the account number and bank
  code, and show the resolved `accountName` back to whoever entered it — this is
  how you catch a typo'd account number before money is on the line.

  3. Call `POST /subwallet/create` to create a subwallet — a way to segregate
  funds under your own merchant account (per department, storefront, or
  sub-brand), not a customer's wallet. The response includes a dedicated virtual
  account; funds sent to it land in this subwallet, separate from your main
  wallet balance. Save the returned `id` — there's no lookup-by-`reference`
  endpoint here, only the list endpoint below.

  4. Call `GET /subwallets` to list all subwallets on your account. This always
  returns the full set — there's no pagination on this endpoint, unlike the
  TrustCore/TrustVault listing endpoints.
hidden: false
---