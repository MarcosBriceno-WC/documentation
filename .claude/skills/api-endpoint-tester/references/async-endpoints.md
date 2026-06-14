# Async Endpoints

> **How to use this file:** List any endpoints whose primary payload is
> delivered via webhook rather than in the HTTP response. The skill checks
> this file before testing an endpoint. If an endpoint is listed here, a
> thin or empty HTTP response (such as `202 Accepted` or `204 No Content`)
> is correct behavior and should not be flagged as a failure or a
> discrepancy.
>
> Webhook payload validation is handled by a separate companion skill.
> This file exists solely to prevent the tester from misreading an
> intentionally minimal HTTP response as a bug.
>
> Add entries here from client briefings or when discovered during testing.

---

## Async Endpoint List

| Method | Path | Expected HTTP response | Webhook event name | Notes |
|---|---|---|---|---|
| | | | | |

---

## Notes

<!-- Any general notes about the async pattern used by this API. For
example: whether retries are supported, whether the webhook payload
includes the full resource or just an event reference, etc. -->