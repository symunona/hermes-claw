# app

Capacitor client app responsible for:

- Scanning/opening pairing QR links
- Registering passkeys (platform authenticator)
- Signing authentication challenges
- Opening authenticated WebSocket sessions

## Suggested stack

- Capacitor + TypeScript
- Native passkey bridge/plugin (iOS AuthenticationServices, Android Credential Manager)
- Secure local storage for session tokens only (never private keys)
