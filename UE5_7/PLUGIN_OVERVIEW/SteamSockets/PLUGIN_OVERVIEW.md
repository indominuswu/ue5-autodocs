# Steam Sockets Plugin Overview

## 1. What this plugin does
- Implements a SteamSockets-based networking backend using Steamworks’ modern socket API.
- Provides a dedicated `SteamSockets` socket subsystem, net driver, and net connection classes for Steam relay or direct transport.
- Requires the Steam net driver configuration; depends on `OnlineSubsystem`, `OnlineSubsystemSteam`, and `SteamShared`.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Networking teams configure `USteamSocketsNetDriver`/`USteamSocketsNetConnection` via the SteamSockets subsystem to use SteamNetworkingSockets transport.

## 3. Key Modules
- **SteamSockets** (Runtime) – Socket subsystem implementation, net driver/connection classes, and Steam task manager for SteamNetworkingSockets transport.

## 4. Important Types & APIs
- `FSteamSocketsSubsystem` – `ISocketSubsystem` + ticker/exec that creates sockets, resolves addresses, tracks relay usage, and routes Steam socket events; exposes helper methods to link sockets with net drivers and query identity.
- `USteamSocketsNetDriver` / `USteamSocketsNetConnection` – Net driver/connection types bound to the SteamSockets transport.
- `FSteamSocket` / `SteamSocketHandles` / `FSteamSocketsTaskManagerInterface` – Internal transport helpers for sending/receiving over Steam’s networking sockets.
- `FInternetAddrSteamSockets` (via `IPAddressSteamSockets.h`) – Steam-specific internet address implementation for the subsystem.

## 5. Typical usage patterns
- Enable the plugin alongside OnlineSubsystemSteam and configure the project/game `DefaultEngine.ini` to use `SteamSocketsNetDriver` for networking.
- Use the subsystem only with its paired net driver/connection; mixing with other net drivers is unsupported.
- Optional relay usage is controlled via Steam settings; subsystem tracks login state and relay enablement.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; behaviors are based on the current plugin source.

