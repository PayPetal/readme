---
title: Update a Customer
api:
  file: paypetal-api.json
  operationId: get_apiv1customer{customerId}
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
This endpoint updates an existing customer’s details.
It allows you to correct user information without creating a new record.

Purpose
Use this to change contact details or update names when a customer modifies their information in your system.

Key Notes
•	All fields are optional, but at least one must be provided for an update to occur.
•	If the customerId does not exist, the API returns an error.
•	The operation does not affect existing transactions linked to that customer.

Typical Use Case
•	When a customer updates their contact email in your dashboard.
•	When an administrator modifies customer data during a support request.
