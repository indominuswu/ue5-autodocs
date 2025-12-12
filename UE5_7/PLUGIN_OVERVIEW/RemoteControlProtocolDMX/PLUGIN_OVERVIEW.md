# Remote Control Protocol DMX Plugin Overview

## 1. What this plugin does
- Bridges Remote Control presets with DMX, letting DMX universes drive exposed properties/controllers.
- Maintains per-preset DMX library proxies and fixture patch mappings.
- Provides editor tooling to auto-build DMX libraries, bind patches to exposed entities, and customize preset user data.

## 2. Editor/Runtime surfaces

- User-facing: Yes - DMX protocol integration for Remote Control with editor widgets/proxies (`URemoteControlDMXLibraryProxy`, patch builders) that users configure to map DMX fixtures to exposed properties.

## 3. Key Modules
- **RemoteControlProtocolDMX** (Runtime)  
  - Implements the DMX protocol for Remote Control; manages preset-bound DMX library proxies, patch observers, and runtime handling of fixture data.
- **RemoteControlProtocolDMXEditor** (Editor)  
  - Details customizations, patching widgets, auto-bind handlers, and per-preset editor settings for DMX bindings.

## 4. Important Types & APIs
### `URemoteControlDMXLibraryProxy`
- Role: Transient object per preset that owns/updates the DMX library and property patches; listens to fixture patch data and preset exposure changes.
- Key functions: `GetDMXLibrary()`, `Refresh/Reset`, `GetPropertyPatches()`, editor delegates for pre/post patch changes.

### `URemoteControlDMXUserData`
- Role: UObject stored with presets to keep DMX patch grouping/mode and references to fixture data; collaborates with the proxy.

### `FRemoteControlProtocolDMX`
- Role: Protocol implementation mapping DMX channel data to Remote Control protocol entities.

### Editor helpers
- `URemoteControlDMXPerPresetEditorSettings` and UI widgets (`SRemoteControlDMXExposedEntityPatch`, `...GroupPatch`) manage patch assignment UX.
- Library/patch builders (`FRemoteControlDMXLibraryBuilder`, `FRemoteControlDMXPatchBuilder`) automate fixture creation from preset data.

## 5. Typical usage patterns
- Enable Remote Control and DMX plugins, then enable this protocol.
- In the Remote Control Panel, choose DMX as the protocol for exposed entities; use the DMX patch widgets to select fixture types and patch ranges.
- Use the auto-bind handler to create bindings from incoming DMX signals or to generate fixture patches matching preset exposure.
- At runtime, incoming DMX data updates exposed properties via the protocol entities maintained by the proxy.

## 6. Version-specific notes (UE 5.7)
- `URemoteControlProtocolDMXSettings` is marked deprecated (commented as of 5.5) and is not registered as project settings; use per-preset/editor settings instead.
- No other UE 5.7-specific behaviors surfaced in source.

