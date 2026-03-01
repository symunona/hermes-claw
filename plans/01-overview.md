# 01 - Overview

## Goal

Expose a simple internet-facing channel with:

1. QR-based one-time pairing
2. Device-bound authentication via passkeys (or asymmetric keys)
3. Short-lived session tokens for WebSocket access

## Security principles

- Private key never leaves phone
- Server stores only public credentials
- Pairing tickets are short-lived and single-use
- WebSocket tokens are short-lived and scoped
- No recovery flow; reset means re-pair from scratch
