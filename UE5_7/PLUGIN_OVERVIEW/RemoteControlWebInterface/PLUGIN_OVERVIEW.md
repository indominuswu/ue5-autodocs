# Remote Control Web Interface Plugin Overview

## 1. What this plugin does
- Supplies a web-based UI for Remote Control presets; relies on the core Remote Control servers.
- Offers Blueprint helpers to locate actors, owners, and rebind preset properties for the web client workflow.

## 2. Key Modules
- **RemoteControlWebInterface** (Runtime)  
  - Web interface integration plus Blueprint utilities to support rebinding and actor discovery used by the web app.

## 3. Important Types & APIs
### `URCWebInterfaceBlueprintLibrary`
- Role: Blueprint helper library to support the web UI’s rebinding flow.
- Key functions: `FindMatchingActorsToRebind(PresetId, PropertyIds)`, `GetOwnerActorLabel(...)`, `RebindProperties(...)`, `FindAllActorsOfClass`, `SpawnActor`, `GetValuesOfActorsByClass`.
- Helpers retrieve `URemoteControlPreset` internally for lookup and rebinding.

## 4. Typical usage patterns
- Enable Remote Control, WebRemoteControl, and this plugin.
- Build/serve the Remote Control web app (per `URemoteControlSettings`), then use the Blueprint helpers for custom web workflows (e.g., expose new rebind options or actor queries).
- Web clients use preset IDs to request property rebinding or actor value snapshots.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

