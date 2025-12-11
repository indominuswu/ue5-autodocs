# Remote Control API Plugin Overview

## 1. What this plugin does
- Provides runtime and editor tooling to expose actors, properties, and functions through `Remote Control Preset` assets.
- Hosts HTTP and WebSocket servers (WebRemoteControl) so external tools can drive exposed fields.
- Supplies UI panels and Multi-User support for authoring presets and protocol bindings in the editor.
- Abstracts control protocols (e.g., DMX, MIDI, OSC) via a protocol layer with editor widgets for binding.

## 2. Key Modules
- **RemoteControl** (Runtime)  
  - Core preset asset, exposure logic, and controllers; `URemoteControlPreset` authoring/runtime APIs.
- **RemoteControlLogic** (Runtime)  
  - Logic/virtual property utilities used by presets and controllers.
- **WebRemoteControl** (Runtime)  
  - HTTP/WebSocket servers for preset access; request preprocessing/authorization.
- **RemoteControlCommon** (Runtime)  
  - Shared settings (`URemoteControlSettings`), property utilities, and preset metadata helpers.
- **RemoteControlProtocol** (Runtime)  
  - Protocol abstraction for binding external signals to preset entities.
- **RemoteControlUI** (Editor)  
  - Remote Control Panel, toolbar/menu integration, preset toolkit, and settings UI.
- **RemoteControlProtocolWidgets** (Editor)  
  - Details/custom widgets for protocol bindings.
- **RemoteControlMultiUser** (UncookedOnly)  
  - Multi-User collaboration hooks for presets and protocol transactions.

## 3. Important Types & APIs
### `URemoteControlPreset`
- Role: Asset containing exposed actors/properties/functions and associated controllers; supports grouping, rebinding, and delegation events.
- Key functions: `ExposeActor`, `ExposeProperty`, `ExposeFunction`, transient preset creation/destruction, controller add/remove/rename events, GUID renewal guards, and change delegates (`OnEntityExposed`, `OnEntitiesUpdated`, etc.).
- Supports embedded presets and rebinding of exposed entities.

### `ARemoteControlPresetActor`
- Role: Actor wrapper that owns a `URemoteControlPreset` instance placed in-level for runtime access.

### `URCPropertyContainerRegistry` (EngineSubsystem)
- Role: Manages remote control property containers available in the engine for lookup and binding.

### `URemoteControlSettings` (Developer Settings, config=`RemoteControl`)
- Security and server controls: allowed/blocked client ranges, passphrase requirements, allowed origins, python/console execution toggles.
- Web interface/server defaults: bind addresses/ports, auto-start flags, logging options.
- Preset UI defaults: panel layout splits, warning toggles, exposed-entity columns, logic panel visibility.

### Protocol and Web components
- `IRemoteControlProtocolModule` / `IRemoteControlProtocol` interfaces: apply/unapply bindings for presets and create protocol entities.
- Web preprocessors (in WebRemoteControl) enforce `URemoteControlSettings` security before servicing requests.

## 4. Typical usage patterns
- Editor: enable the plugin, open the Remote Control Panel, create a `Remote Control Preset`, expose actors/properties/functions, group them, and save the asset. Configure security and server ports in Project Settings → Plugins → Remote Control.
- Runtime/control: start WebRemoteControl servers (auto-start via settings), query presets over HTTP/WS, and set controller values. Use `ARemoteControlPresetActor` to host presets in a world.
- Protocol bindings: install protocol plugins (DMX/MIDI/OSC, etc.), open the binding tab, and map incoming protocol channels to exposed entities. Use protocol widgets to configure device/patch settings.
- Multi-user workflows: enable `RemoteControlMultiUser` so preset edits and protocol transactions replicate in Multi-User sessions.

## 5. Version-specific notes (UE 5.7)
- Deprecated flag `bProtocolsGenerateTransactions_DEPRECATED` (noted in `URemoteControlSettings`) indicates per-preset protocol transaction control supersedes the old global toggle.
- No additional UE 5.7-specific behaviors surfaced; overview reflects the current source.

