# 02 - QR Pairing Spec

## Why short-lived QR codes

A QR is a temporary pairing ticket, not a long-term secret.

- Limits damage from screenshots/interception
- Prevents replay after use
- Reduces log leakage risk

## Ticket model

`pair_ticket` fields:

- `pair_id` (random, high entropy)
- `created_at`
- `expires_at` (e.g. +90s)
- `used` (bool, default false)
- `bound_client_nonce` (optional)
- `requested_by` (optional telemetry)

## Flow

1. Web requests `POST /pair/start`.
2. Server creates `pair_ticket` and returns `pair_url`.
3. Web renders QR of `pair_url`.
4. Phone opens QR URL and starts passkey registration/auth.
5. Server marks ticket `used=true` immediately after successful completion.
6. Any reuse or expired ticket => reject.

## Validation rules

- Reject if now > `expires_at`
- Reject if `used=true`
- Reject if origin/app binding mismatch
- Rate-limit by IP/device
