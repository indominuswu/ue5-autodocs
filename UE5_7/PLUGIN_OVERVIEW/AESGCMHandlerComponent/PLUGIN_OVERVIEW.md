# AES GCM Network Packet Handler Plugin Overview

## 1. What this plugin does
- Adds a packet handler component that encrypts/decrypts network packets using AES-GCM.
- Provides optional fault handler for error reporting and recovery.
- Useful for secure transport on top of existing UE networking.

## 2. Key Modules
- **AESGCMHandlerComponent** (Runtime)
  - Role: Implements AES-GCM packet handler and related fault handling.

## 3. Important Types & APIs

### `FAESGCMHandlerComponent`
- Role: Packet handler that wraps network traffic with AES-GCM encryption/decryption.

### `FAESGCMFaultHandler`
- Role: Detects and reports issues (e.g., auth failures) during AES-GCM processing.

## 4. Typical usage patterns
- Enable the plugin and register the AES-GCM packet handler in network ini/settings.
- Configure keys and handler options per project network configuration.
- Use alongside other packet handlers to secure replication traffic.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.