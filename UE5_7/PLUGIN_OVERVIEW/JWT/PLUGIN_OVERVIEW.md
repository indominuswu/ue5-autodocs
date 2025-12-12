# JSON Web Token Plugin Overview

## 1. What this plugin does
- Implements JSON Web Token (JWT) creation and verification utilities using PlatformCrypto.
- Exposes JWT parsing, header/payload manipulation, and signing/verification helpers.
- Ships with unit tests covering algorithms and parsing.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Runtime JWT API (`FJsonWebToken`/`IJwt`, `FJwtAlgorithms`) developers use to create, sign, and verify tokens.

## 3. Key Modules
- **JWT** (Runtime) - Core JWT API and tests.

## 4. Important Types & APIs
### `IJwt`
- Role: Interface for encoding and decoding JWTs.

### `FJsonWebToken`
- Role: Concrete token representation exposing header/payload accessors and validation helpers.

### `FJwtAlgorithms` / `FJwtAlgorithm`
- Role: Algorithm registry and helpers (e.g., HMAC) used for signing/verification.

### `FJwtUtils`
- Role: Utility helpers for base64url handling, claim extraction, and validation helpers.

## 5. Typical usage patterns
- Enable the plugin and include the JWT module in your target.
- Use `FJsonWebToken`/`IJwt` to parse tokens, set claims, and sign or verify using supported algorithms.
- PlatformCrypto is required for cryptographic operations.

## 6. Version-specific notes (UE 5.7)
- No explicit 5.7-only changes; plugin remains experimental but functional in 5.7.

