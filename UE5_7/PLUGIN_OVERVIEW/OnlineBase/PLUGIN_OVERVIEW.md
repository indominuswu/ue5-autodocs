# Online Base Plugin Overview

## 1. What this plugin does
- Supplies shared utilities for legacy Online Subsystem (OSSv1) and Online Services (OSSv2).
- Provides network byte-order serializers and LAN beacon/session helper classes.
- Acts as a foundational runtime dependency for online platform plugins.

## 2. Editor/Runtime surfaces

- User-facing: No - Infrastructure layer (serializers, LAN beacon helpers) used by online subsystems; no editor UI or Blueprint-level gameplay features for end users.

## 3. Key Modules
- **OnlineBase** (Runtime): Core serialization utilities and LAN discovery helpers.

## 4. Important Types & APIs
### `FNboSerializeToBuffer` / `FNboSerializeFromBuffer`
- Role: Network byte-order serializers for reading/writing primitive types and enums.
### `FLanBeacon` / `FLANSession`
- Role: LAN discovery helpers handling beacon sockets, broadcast addresses, and response handling.
### `OnlineSessionNames`
- Role: Centralized definition of common online session identifiers used across subsystems.

## 5. Typical usage patterns
- Used transitively by OnlineSubsystem/OnlineServices implementations for packet serialization and LAN discovery.
- Call LAN beacon helpers to search for local sessions or advertise a host over broadcast sockets.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; serves as the baseline online utility layer.

