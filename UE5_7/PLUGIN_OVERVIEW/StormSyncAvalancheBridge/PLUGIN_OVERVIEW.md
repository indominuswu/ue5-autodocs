# Storm Sync Motion Design Bridge Plugin Overview

## 1. What this plugin does
- Bridges Motion Design (Avalanche) workflows with Storm Sync to synchronize assets directly from the Motion Design toolset.
- Adds runtime glue plus editor extensions so Motion Design content can be pushed/pulled through Storm Sync without leaving the editor.

## 2. Key Modules
- **StormSyncAvaBridge** (Runtime) – Runtime bridge that exposes Storm Sync integration points to Motion Design (client-only; denied on dedicated servers).
- **StormSyncAvaBridgeEditor** (Editor) – Editor hooks and UI/commands that register the Motion Design sync provider.

## 3. Important Types & APIs
- `FStormSyncAvaSyncProvider` (ModularFeature) – Registers Motion Design as a Storm Sync provider, wiring asset sync requests into Storm Sync transports.
- Utility headers (`StormSyncAvaBridgeUtils`, `StormSyncAvaBridgeCommon`) – Shared helpers/constants for bridge behavior and logging.
- Editor extensibility (`FStormSyncAvaRundownExtender`) – Extends Motion Design rundown UI to expose Storm Sync actions.

## 4. Typical usage patterns
- Enable both Motion Design (`Avalanche`) and `StormSync` along with this bridge.
- Use Motion Design UI; the bridge registers a sync provider so rundown items can be synchronized through Storm Sync transports.
- Runtime module is client-only; server builds ignore the bridge.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; bridge is marked experimental/beta via module defaults.

