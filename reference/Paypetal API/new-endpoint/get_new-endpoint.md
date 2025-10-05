---
title: Authentication
excerpt: This is your first endpoint! Edit this page to start documenting your API.
api:
  file: paypetal-api.json
  operationId: get_new-endpoint
hidden: false
---
<br />

## Authentication

### Bearer Token

All endpoints require a valid Bearer Token in the header.

Use the login endpoint to obtain your token.

### POST `/api/auth/login`

Authenticate merchant and generate access token.

**Description**
Generate a token using your base64 encoded developer secret key and application ID.
Format: `developer_secret_key:application_id`.

**Content Type**: `application/json`

**Request**

```
{
  "base64Hashed": "ZGV2ZWxvcGVyX3NlY3JldDphcHBsaWNhdGlvbl9pZA=="
}
```

**Response**
