---
title: Authenticate Merchant
excerpt: >-
  This endpoint allow merchant to generate token. The token will be used to
  authenticate other endpoints. To generate token, merchant must provide base64
  encoded developer secret key and application id in the request body. the
  base64 encoded string should be in the format of
  'developer_secret_key:application_id'.
api:
  file: openai_fixed.yml
  operationId: login
hidden: false
---