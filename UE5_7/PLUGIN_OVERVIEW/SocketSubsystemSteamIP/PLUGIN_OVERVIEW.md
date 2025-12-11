# Socket Subsystem Steam (IP) Plugin Overview

## 1. What this plugin does
- Supplies a Steam-backed socket subsystem for IP-based networking (non-NAT traversal).
- Provides Steam-specific net driver and connection classes for projects using Steam networking without SteamSockets P2P.
- Targets Win64/Mac desktop platforms (excluding Win64 ARM64).

## 2. Key Modules
- **SocketSubsystemSteamIP** (RuntimeNoCommandlet)
  - Role: Registers the Steam IP socket subsystem and implements Steam net driver/connection support.
  - Notable types: `USteamNetDriver`, `USteamNetConnection`, `FSocketSubsystemSteam` helpers.

## 3. Important Types & APIs
- `USteamNetDriver` (extends `UIpNetDriver`)
  - Role: Net driver implementation that talks to Steam sockets for IP connections.
- `USteamNetConnection` (extends `UIpConnection`)
  - Role: Connection class used by the Steam net driver; overrides setup for local/remote endpoints.
- `FSocketSubsystemSteam`
  - Role: Subsystem registration/management; tracks active `USteamNetConnection` instances.

## 4. Typical usage patterns
- Enable the plugin with `OnlineSubsystemUtils` and `SteamShared`.
- Configure the project or specific net drivers to use `USteamNetDriver` when Steam IP transport is desired.
- Use only for direct IP connectivity; for NAT punchthrough/P2P, switch to the SteamSockets plugin instead.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
