---
description: >-
  Understand the API rate limits that apply to your plan, and what to do if you
  hit them.
icon: gauge-high
---

# API rate limits and quotas

Rate limits protect platform stability and ensure fair usage across all customers. If you're building an integration or automation on top of our API, it's worth understanding how they work.

### Limits by plan

| Plan       | Requests per minute | Requests per day |
| ---------- | ------------------- | ---------------- |
| Free       | 60                  | 1,000            |
| Pro        | 300                 | 10,000           |
| Business   | 1,000               | 100,000          |
| Enterprise | Custom              | Custom           |

### Rate limit headers

Every API response includes headers showing your current usage:

```
X-RateLimit-Limit: 300
X-RateLimit-Remaining: 241
X-RateLimit-Reset: 1714560000
```

`X-RateLimit-Reset` is a Unix timestamp indicating when your limit resets.

### What happens when you hit the limit

Requests that exceed the rate limit receive a `429 Too Many Requests` response. Your client should back off and retry after the time indicated in the `Retry-After` header.

{% hint style="warning" %}
Repeatedly hammering the API after receiving a 429 may result in a temporary ban on your API key. Always implement exponential backoff in your integration.
{% endhint %}

### Increasing your limits

If your use case requires higher limits, upgrading your plan is the first step. For Enterprise-level requirements, [contact us](https://example.com/contact) to discuss custom quotas.
