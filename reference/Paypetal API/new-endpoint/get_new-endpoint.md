---
title: Authentication
excerpt: >-
  This endpoint lets merchants make an access token, which is needed for all
  secure PayPetal API calls.  The access token is a temporary credential that
  lets PayPetal check who the merchant is and provide them access to its
  endpoints.  If you don't have a valid token, every call to protected endpoints
  will fail with a "unauthorised" error.
api:
  file: paypetal-api.json
  operationId: get_new-endpoint
hidden: false
---
Before utilising any other API endpoint, merchants must verify their identity.  Only registered and verified developers or merchants can make payments, set up escrow agreements, or manage clients on the PayPetal platform.

The authentication endpoint gives out a JSON Web Token (JWT).  This token is different for each session, and any API calls after that must use the Bearer format to include it in the header.

<br />

# How to Generate Base64 Value for Authentication

Before you can log in or use any PayPetal API endpoint, you must include a `base64Hashed` value in your authentication request.
This value securely encodes your developer credentials.

***

## Step 1: Get Your Credentials

You will receive two credentials from PayPetal:

* **Developer Secret Key**
* **Application ID**

**Example**

```
Developer Secret Key: dev_7f4b33a1
Application ID: app_14279
```

***

## Step 2: Combine the Values

Join both values using a colon `:` in between.

**Format**

```
developer_secret_key:application_id
```

**Example**

```
dev_7f4b33a1:app_14279
```

***

## Step 3: Convert to Base64

Convert the combined string to Base64 format. You can do this using one of the methods below.

### Option 1: Online Encoder

1. Go to a trusted Base64 encoder website.
2. Paste `dev_7f4b33a1:app_14279` in the input box.
3. Click **Encode**.
4. Copy the generated output.

**Example Output**

```
ZGV2XzdmNGIzM2ExOmFwcF8xNDI3OQ==
```

***

### Option 2: macOS or Linux Terminal

Run:

```
echo -n "dev_7f4b33a1:app_14279" | base64
```

**Output**

```
ZGV2XzdmNGIzM2ExOmFwcF8xNDI3OQ==
```

***

### Option 3: Windows PowerShell

Run:

```
[Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes("dev_7f4b33a1:app_14279"))
```

***

### Option 4: Python

```python
import base64
encoded = base64.b64encode("dev_7f4b33a1:app_14279".encode()).decode()
print(encoded)
```

***

### Option 5: JavaScript

```javascript
console.log(btoa("dev_7f4b33a1:app_14279"));
```

***

## Step 4: Add Base64 to Your API Request

Use the encoded string as the value for `base64Hashed` in your request body.

**Example**

```
base64Hashed=ZGV2XzdmNGIzM2ExOmFwcF8xNDI3OQ==
```

***

## Step 5: Authenticate

Send the POST request to:

When successful, the server will return your **Bearer token**.
Use this token in the `Authorization` header for all subsequent API calls.

<br />
