---
title: Create Customer
api:
  file: paypetal-api.json
  operationId: post_apiv1customer
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
This endpoint registers a new customer under your merchant account.
A customer must exist before you can create an escrow agreement or process payments on their behalf.

Purpose
Use this to onboard a new buyer, vendor, or client into your system.
Once created, the customerId becomes the permanent reference key for all future operations related to that customer.