# DTLS network packet handler Plugin Overview

## 1. What this plugin does
- Adds a DTLS-based packet handler component for Unreal networking.
- Provides encryption/decryption of UDP traffic using Datagram TLS as part of the PacketHandler pipeline.
- Intended for titles that need secure transport without rewriting the networking stack.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Runtime packet handler (`DTLSHandlerComponent` module, opt-in via `PacketHandlerComponents` config) that developers add to secure UDP traffic with DTLS.

## 3. Key Modules
- **DTLSHandlerComponent** (Runtime)  
  - Role: Implements the DTLS packet handler and ties into the engine PacketHandlers.

## 4. Important Types & APIs
- The module plugs into the packet handler registry; core types are internal to the module. No Blueprint-facing subsystems or components are exposed.

## 5. Typical usage patterns
- Enable the plugin and configure the packet handler chain (e.g., via `DefaultEngine.ini` PacketHandlerComponents) to include the DTLS handler.
- Use for secure client/server UDP traffic; otherwise behaves transparently once configured.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

