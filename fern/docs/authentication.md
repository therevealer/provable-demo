---
title: Authentication
description: How to authenticate with the Provable API
---

# Authentication

Some Provable API endpoints are public and require no authentication. 
Others — including Delegated Proving, Record Scanning, and higher rate limit tiers — 
require a JWT token.

## Get access

Register for an API account by emailing [explorer@provable.com](mailto:explorer@provable.com) 
or using the registration endpoint directly.

## Register via API
```bash
curl -X GET https://api.provable.com/v2/mainnet/auth/register \
  -H "Content-Type: application/json"
```

This returns your credentials for issuing a JWT.

## Issue a JWT

Once registered, issue a signed JWT token:
```bash
curl -X POST https://api.provable.com/v2/mainnet/auth/jwt \
  -H "Content-Type: application/json" \
  -d '{"username": "your_username", "password": "your_password"}'
```

**Response:**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

## Use your token

Pass the JWT as a Bearer token in the `Authorization` header:
```bash
curl https://api.provable.com/v2/mainnet/prove \
  -H "Authorization: Bearer YOUR_JWT_TOKEN"
```

<Warning>
  Keep your JWT token private. Do not expose it in client-side code or public repositories.
</Warning>

## Token expiry

JWTs expire after a set period. Re-issue a new token using the same credentials 
when yours expires.