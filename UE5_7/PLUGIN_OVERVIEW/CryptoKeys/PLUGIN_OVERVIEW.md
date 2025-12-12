# CryptoKeys Plugin Overview

## 1. What this plugin does

- Manages encryption key generation/configuration for projects and provides a commandlet for key operations.
- Integrates with project settings and build mutators to embed/use generated keys.
- Enabled by default on Win64/Mac/Linux.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users generate/configure crypto keys in Project Settings or via the CryptoKeys commandlet; the plugin’s build mutator injects keys for packaging on Win64/Mac/Linux.

## 3. Key Modules

- **CryptoKeys** (Editor, Default)  
  - Role: Settings UI, commandlet, helpers, and build mutator for crypto keys.  
  - Notable types: `FCryptoKeysModule`, `UCryptoKeysSettings`, `UCryptoKeysCommandlet`, `FCryptoKeysProjectBuildMutatorFeature`, `FCryptoKeysHelpers`, `FCryptoKeysSettingsDetails`.

- **CryptoKeysOpenSSL** (Editor, Default)  
  - Role: OpenSSL-backed implementation for cryptographic operations (module compiled per platform allow list).

## 4. Important Types & APIs

- `UCryptoKeysSettings`: Project settings for key generation/storage.  
- `UCryptoKeysCommandlet`: Commandlet to manage keys from the command line.  
- `FCryptoKeysProjectBuildMutatorFeature`: Inserts necessary crypto config during builds.  
- `FCryptoKeysHelpers`: Utility helpers for key handling.  
- Details customization for settings UI (`FCryptoKeysSettingsDetails`).

## 5. Typical usage patterns

- Configure encryption keys in Project Settings (Crypto Keys); generate/distribute keys for packaged builds.  
- Run the CryptoKeys commandlet to manage keys from scripts/CI.  
- Let the build mutator embed appropriate crypto data during packaging.

## 6. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted; reflects current crypto tooling.

