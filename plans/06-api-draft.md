# 06 - API Draft

## Pairing

- `POST /pair/start` -> create ticket + return `pair_url`
- `GET /pair/:pair_id/status` -> pending|paired|expired|used

## WebAuthn

- `POST /webauthn/register/options`
- `POST /webauthn/register/verify`
- `POST /webauthn/auth/options`
- `POST /webauthn/auth/verify` -> returns short-lived `ws_token`

## WebSocket

- `GET /ws` (upgrade with bearer token)
- Server emits progress and response events

## Reset

- `POST /auth/reset` -> clear credentials + revoke sessions
