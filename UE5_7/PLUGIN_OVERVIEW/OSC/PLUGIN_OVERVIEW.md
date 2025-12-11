# OSC (Open Sound Control) Plugin Overview

## 1. What this plugin does

- Implements OSC 1.0 message and bundle support for sending/receiving OSC traffic between Unreal and external apps/devices.
- Provides runtime client/server classes, address parsing, and packet serialization for UDP-based OSC communication.

## 2. Key Modules

- **OSC** (Runtime)  
  - Role: Runtime transport, serialization, and management of OSC endpoints.

## 3. Important Types & APIs

- `UOSCClient`, `UOSCServer` (`OSCClient.h`, `OSCServer.h`)  
  - High-level Blueprint-accessible endpoints for sending and receiving OSC messages.
- `UOSCManager`  
  - Manages active clients/servers and address routing.
- `FOSCMessage`, `FOSCBundle`, `FOSCAddress`, `FOSCPacket`  
  - Data structures for building and parsing OSC payloads.
- `AOSCServerReceiver` / proxy classes (`OSCServerProxy.h`, `OSCClientProxy.h`)  
  - Lower-level networking helpers for message dispatch.

## 4. Typical usage patterns

- Enable the plugin, then create OSC Server/Client objects in Blueprints or C++ to bind to ports and send/receive messages.
- Use `UOSCManager` to register addresses and route incoming messages to handlers.
- Common for live performance, virtual production, and DCC tool integration over UDP.
- No dedicated editor UI; configuration is done in code/Blueprints and project settings for network access.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview reflects the OSC implementation in the UE 5.7 source tree.
