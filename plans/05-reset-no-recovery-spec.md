# 05 - Reset / No-Recovery Spec

## Policy

No account recovery paths.

- No backup codes
- No email reset
- No secondary secret fallback

## Reset behavior

Reset invalidates all trusted credentials and sessions:

1. Delete stored passkey credentials for user/device scope
2. Revoke active tokens/sessions (`jti` denylist or session version bump)
3. Require fresh QR pairing and passkey registration

## Admin/safety controls

- Reset endpoint requires strong operator auth
- Audit log each reset event with timestamp and actor
- Optional cooldown for repeated reset attempts
