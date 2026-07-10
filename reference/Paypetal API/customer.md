---
title: Customers
deprecated: false
hidden: false
metadata:
  robots: index
next:
  pages:
    - slug: create-customer
      title: Create Customer
      type: endpoint
---
The Customers API is a core part of the PayPetal Merchant Platform.
It allows merchants to create, manage, update, and remove customers from their account.
Every customer record serves as a link between your business and the buyer in escrow or payment transactions.

When you create a customer, PayPetal assigns a unique customerId.
This ID is used to associate that customer with future payments, escrow agreements, and transaction records.
The Customers API ensures you have full control over your client database through standard REST endpoints.

All customer-related endpoints require authentication with a Bearer Token.
Include it in your request headers for every operation:

<br />

```
Authorization: Bearer <your_jwt_token>
```

<br />
