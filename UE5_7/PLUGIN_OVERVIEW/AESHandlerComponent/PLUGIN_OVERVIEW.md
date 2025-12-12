# AES Network Packet Handler Plugin Overview

## 1. What this plugin does
- Provides a packet handler component for AES encryption/decryption of network packets.
- Lightweight alternative to the AES-GCM variant when authentication/tagging is not required.

## 2. Editor/Runtime surfaces
- User-facing: No - runtime-only AES packet handler (`FAESHandlerComponent`) added via network handler lists; no editor UI, Blueprint library, or gameplay-facing surface.

## 3. Key Modules
- **AESHandlerComponent** (Runtime)
  - Role: Implements AES-based packet handler for network traffic.

## 4. Important Types & APIs

### `FAESHandlerComponent`
- Role: Encrypts and decrypts packets using configured AES keys in the packet handler chain.

## 5. Typical usage patterns
- Enable the plugin and add the AES handler to your network configuration (e.g., via ini packet handler list).
- Supply encryption keys through project/network settings to secure replication traffic.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
