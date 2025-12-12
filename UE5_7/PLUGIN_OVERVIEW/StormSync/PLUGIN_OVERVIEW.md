# Storm Sync Plugin Overview

## 1. What this plugin does
- Virtual Production asset synchronization toolkit for pulling/pushing assets and dependencies.
- Provides drive mounting, transport (TCP/UDP) discovery, and import subsystems to move assets between machines.
- Includes editor notifications and tooling; integrates with Content Browser data sources.
- Recommended for Motion Design workflows but usable generally for asset sync.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor sync tools/notifications plus runtime subsystems for transferring and importing assets across machines.

## 3. Key Modules
- **StormSyncCore** (Runtime) – Core sync logic and configuration.
- **StormSyncDrives** (Runtime) – Drive mounting and settings for shared sync locations.
- **StormSyncTransportCore/Client/Server** (Runtime) – Network transport utilities, settings, client/server sockets, and discovery for pushing/pulling packages.
- **StormSyncImport** (Runtime) – Engine/world subsystems that consume incoming packages and trigger imports.
- **StormSyncEditor** (Editor) – Editor UI, notifications, and commands.
- **StormSyncTests** (UncookedOnly) – Test helpers.

## 4. Important Types & APIs
- `UStormSyncCoreSettings`, `UStormSyncDrivesSettings`, `UStormSyncTransportSettings` – Developer settings controlling default sync paths, mounted drives, network endpoints/ports, and discovery addresses.
- `UStormSyncImportSubsystem` (EngineSubsystem) / `UStormSyncImportWorldSubsystem` (WorldSubsystem) – Handle incoming Storm Sync packages and world-level import hooks.
- `UStormSyncNotificationSubsystem` (EditorSubsystem) – Editor toast/notification routing for sync events.
- Transport helpers: `FStormSyncDiscoveryManager` (server discovery), `FStormSyncTransportClientSocket` / `FStormSyncTransportServer` classes manage TCP/UDP session lifecycle and handshake.
- Command utilities (`StormSyncTransportCommandUtils`, `StormSyncTransportNetworkUtils`) resolve addresses and generate CLI parameters for sync endpoints.

## 5. Typical usage patterns
- Enable the plugin and configure developer settings for drives and transport (unicast address/ports inherit from UDP Messaging by default).
- Use editor tools to push/pull assets; notifications surface progress via `UStormSyncNotificationSubsystem`.
- Deploy server/client transport modules on target machines; discovery broadcasts server availability and imports are handled by the engine/world subsystems.
- Mount remote drives through `UStormSyncDrivesSettings` to keep project paths consistent across machines.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; functionality derives from current runtime/editor modules marked as non-experimental.
