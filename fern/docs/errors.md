---
title: Errors
description: Error codes and how to handle them
---

The Provable API uses standard HTTP status codes. All error responses return 
a JSON body with an `error` field describing what went wrong.

## Error response format
```json
{
  "error": "A human-readable description of the error"
}
```

## HTTP status codes

| Status | Name | Description |
|---|---|---|
| `200` | OK | Request succeeded |
| `400` | Bad Request | Invalid parameters or malformed request |
| `401` | Unauthorized | Missing or invalid JWT token |
| `404` | Not Found | The requested resource does not exist |
| `429` | Too Many Requests | Rate limit exceeded |
| `500` | Internal Server Error | Something went wrong on the server |

## Common errors and fixes

**404 on a transaction ID**
The transaction may not be confirmed yet. Wait a few seconds and retry, 
or check using the unconfirmed transaction endpoint first.

**400 on a program ID**
Program IDs must include the `.aleo` suffix. For example: `token_v1.aleo` not `token_v1`.

**429 Too Many Requests**
You've exceeded 5 requests per second or 100,000 per day. 
Implement exponential backoff and consider caching responses.

**401 Unauthorized**
Your JWT has expired or is malformed. Re-issue a new token using your credentials.