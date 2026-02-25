---
title: Rate Limits
description: Rate limiting rules for the Provable API
---

The Provable API enforces rate limits to ensure fair usage across all developers.

## Default limits

| Limit | Value |
|---|---|
| Requests per second | 5 |
| Requests per day | 100,000 |

These limits apply per API key across all endpoints.

## What happens when you exceed the limit

Requests that exceed the rate limit will receive a `429 Too Many Requests` response:
```json
{
  "error": "Rate limit exceeded. Please slow down your requests."
}
```

## Need higher limits?

If your application requires higher throughput, contact the Provable team at 
[explorer@provable.com](mailto:explorer@provable.com) to discuss increased limits.

<Warning>
  Repeated abuse of rate limits may result in your API key being blacklisted. 
  Implement exponential backoff in your application to handle 429 responses gracefully.
</Warning>

## Best practices

- Cache responses where possible — block data doesn't change once confirmed
- Use the Public API's aggregated endpoints instead of making multiple SnarkOS calls
- Implement retry logic with exponential backoff for production applications