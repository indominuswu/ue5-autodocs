# Remote Control Components Plugin Overview

## 1. What this plugin does
- Experimental components and subsystem that expose actors/properties to the Remote Control framework.
- Provides tracker components and utilities to bind remote control entities to scene properties.
- Includes editor styling and integration hooks.

## 2. Key Modules
- **RemoteControlComponents** (Runtime)
  - Role: Runtime components, subsystem, and utilities for tracking remote control targets (`RemoteControlTrackerComponent`, `RemoteControlTrackerProperty`, `RemoteControlComponentsSubsystem`, `RemoteControlComponentsUtils`).
- **RemoteControlComponentsEditor** (Editor)
  - Role: Editor module and styles for the component UI (`RemoteControlComponentsEditorStyle`).

## 3. Important Types & APIs
### `URemoteControlTrackerComponent`
- Role: Component that monitors actor properties and routes updates to/from Remote Control entities.
- Key properties: tracked properties list, connection to remote control IDs (`RemoteControlTrackerProperty`).

### `URemoteControlComponentsSubsystem`
- Role: Subsystem managing registered tracker components and applying updates across the level.

### `URemoteControlComponentsUtils`
- Role: Helper library for binding/unbinding properties and resolving remote control targets.

## 4. Typical usage patterns
- Enable the plugin alongside Remote Control.
- Add `URemoteControlTrackerComponent` to actors that need to expose properties for remote driving.
- Configure tracker properties to bind to Remote Control entities; run in editor or runtime to propagate updates.
- Use subsystem utilities to manage bindings programmatically.

## 5. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
