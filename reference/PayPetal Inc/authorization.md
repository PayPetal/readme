---
title: Authorization
excerpt: This endpoint allow merchant to generate token.
deprecated: false
hidden: false
metadata:
  robots: index
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

```
{
  "status": true,
  "statusCode": "00",
  "message": "Successful",
  "dataResponse": {
    "accessToken": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJpTlBPR3NYSDF1cFppbVlhQXB3a2VkeXJIWnk3b3F0eW1CNGhDcEZqOHlVPSIsImlhdCI6MTc1OTYxODgwNiwiZXhwIjoxNzYwMjIzNjA2fQ.SS5lu7qYoSnxJyifE1nwxLAUeqLlfxCxcLEg7eugm4A",
    "expireAt": "2025-10-11T23:00:06.951+00:00"
  }
}
```
