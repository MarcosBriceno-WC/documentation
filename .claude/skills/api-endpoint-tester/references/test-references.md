# Test References

> **How to use this file:** Document any special values needed to run
> tests in the staging or sandbox environment. This includes test payment
> cards, magic phone numbers or emails that trigger specific behaviors,
> pre-seeded resource IDs, and staging-only endpoints. The skill reads
> this file at the start of each session and appends new values as they
> are discovered during testing.

---

## Test Credentials

Document test accounts, API keys scoped to specific roles, or sandbox
user credentials.

| Name | Value | Notes |
|---|---|---|
| | | |

---

## Test Payment Methods

If the API involves payment processing, list test card numbers or bank
account details here.

| Card / Account | Number | Expiry | CVV | Behavior |
|---|---|---|---|---|
| Approved Visa | | | | Succeeds |
| Declined card | | | | Returns decline |
| | | | | |

---

## Magic Values

Values that trigger specific API behaviors in staging/sandbox (for
example, specific amounts, phone numbers, or email patterns that simulate
edge cases).

| Value | Where to use it | Behavior triggered |
|---|---|---|
| | | |

---

## Pre-seeded Resource IDs

Resource IDs that exist permanently in the staging environment and can be
reused across sessions (for example, a test customer, a test product).

| Resource type | ID | Notes |
|---|---|---|
| | | |

---

## Staging-only Endpoints

Endpoints that exist only in staging/sandbox to simulate events that
cannot be triggered naturally (for example, simulating a dispute,
triggering a webhook, advancing a subscription billing cycle).

| Endpoint | Method | Purpose |
|---|---|---|
| | | |

---

## Notes

<!-- Any additional context about the test environment, known quirks of
the sandbox, or values that expire and need to be refreshed. -->