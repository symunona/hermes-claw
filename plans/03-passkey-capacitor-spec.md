# 03 - Passkey in Capacitor Spec

## Registration (pair once)

1. App calls `POST /webauthn/register/options` with `pair_id`.
2. Server returns WebAuthn registration challenge/options.
3. App invokes platform passkey API via Capacitor plugin/native bridge.
4. App returns attestation to `POST /webauthn/register/verify`.
5. Server verifies and stores:
   - `credential_id`
   - `public_key`
   - `sign_count`
   - device metadata (minimal)

## Authentication (ongoing)

1. App calls `POST /webauthn/auth/options`.
2. Server returns authentication challenge/options.
3. App signs via platform passkey.
4. App sends assertion to `POST /webauthn/auth/verify`.
5. Server verifies and issues short-lived `ws_token`.

## Platform notes

- iOS: Associated Domains entitlement required
- Android: Digital Asset Links (`assetlinks.json`) required
- RP ID must match your HTTPS domain
- Prefer native passkey UX over custom crypto UI
