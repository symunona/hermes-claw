# server

Backend service responsible for:

- Creating short-lived single-use QR pairing tickets
- Verifying passkey registration/authentication challenges
- Issuing short-lived WebSocket access tokens
- Hosting authenticated WebSocket channels

## Suggested stack

- Node.js + TypeScript
- Express/Fastify for HTTP
- ws/socket.io for realtime
- Redis (optional) for ticket/session state
- `@simplewebauthn/server` for passkey verification
