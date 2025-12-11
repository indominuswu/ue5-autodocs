# Platform Cryptography Plugin Overview

## 1. What this plugin does

- Exposes a unified C++ API for platform-provided cryptography (Android, iOS, macOS, Win64, Linux, PS5, XSX) with OpenSSL fallback.
- Supports AES encryption/decryption contexts (ECB, CBC, GCM) for both engine runtime and standalone programs.
- Ships common types/helpers for block alignment, padding, and secure context lifetime management.

## 2. Key Modules

- **PlatformCrypto** (RuntimeAndProgram)  
  - Role: Module interface (`IPlatformCrypto`) and registration of platform crypto providers.
- **PlatformCryptoTypes** (RuntimeAndProgram)  
  - Role: Fundamental interfaces and enums such as `IPlatformCryptoEncryptor`, `IPlatformCryptoDecryptor`, `EPlatformCryptoResult`, and `FAESBlockEncryptionHelper`.
- **PlatformCryptoContext** (RuntimeAndProgram)  
  - Role: OpenSSL-backed context implementations (`FEncryptionContextOpenSSL`, AES encryptor/decryptor variants) used when native platform APIs are unavailable.

## 3. Important Types & APIs

### `IPlatformCrypto`

- Role: Module interface for requesting encryption/decryption support from the active platform provider.
- Key functions: Factory-style creation of encryptor/decryptor instances, capability checks per algorithm/mode.

### `IPlatformCryptoEncryptor` / `IPlatformCryptoDecryptor`

- Role: Stream-style interfaces for feeding data into AES operations.
- Key functions: `Update`, `Finalize`; implementations handle padding and authentication where applicable.

### `FAESBlockEncryptionHelper`

- Role: Utility that buffers partial blocks so callers can pass arbitrary byte counts to AES encryptors/decryptors safely.
- Key behavior: Retains trailing bytes until a full block is available; flushes/cleans up in `Finalize`.

### `IPlatformCryptoContext` / `FEncryptionContextOpenSSL`

- Role: Context factory that produces encryptors/decryptors backed by OpenSSL EVP APIs when no platform-native crypto is available.
- Notes: Implements AES-256 ECB/CBC/GCM variants; manages EVP contexts with RAII helpers such as `FScopedEVPContext`.

## 4. Typical usage patterns

- Link against `PlatformCrypto` and query the module for a context/encryptor matching your desired AES mode; feed data via `Update`/`Finalize`.
- For game/runtime code, use the module as a drop-in replacement where you would otherwise call OpenSSL directly; the module chooses platform crypto when available.
- For command-line tools (e.g., patchers, cookers), the same APIs are available because modules are marked `RuntimeAndProgram`.
- No Blueprint-facing types; usage is C++ only.

## 5. Version-specific notes (UE 5.7)

- Enabled by default in UE 5.7 for listed platforms; TVOS is explicitly denied in the module allow list.
- No UE 5.7-specific deprecations were identified in source.
