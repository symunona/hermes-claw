# 04 - WebSocket Auth Spec

## Token model

`ws_token` (JWT or opaque):

- TTL: 2-10 minutes
- Claims: `sub`, `sid`, `scope`, `iat`, `exp`, `jti`
- One channel/session scope per token

## Connect flow

1. Client obtains `ws_token` after passkey auth.
2. Client connects `wss://...` with bearer token.
3. Server validates signature, expiry, scope, revocation list.
4. Server upgrades to authenticated socket.

## Runtime events (example)

- `state:queued`
- `state:thinking`
- `state:tool_running`
- `state:done`
- `state:error`

## Hardening

- Enforce TLS (`wss` only)
- Origin checks on handshake
- Per-user and per-IP rate limits
- Idle and absolute session timeouts
