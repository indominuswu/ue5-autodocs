# Motion Design Scene State Integration Plugin Overview

## 1. What this plugin does

- Integrates Motion Design with the Scene State framework to allow Scene State actors to use Avalanche-specific components and players.
- Provides Motion Design-aware Scene State component defaults and editor extensions.

## 2. Key Modules

- **AvalancheSceneState** (Runtime)  
  - Role: Runtime Scene State component/player overrides for Motion Design scenes.
- **AvalancheSceneStateBlueprint** (UncookedOnly)  
  - Role: Blueprint support for the integration.
- **AvalancheSceneStateEditor** (Editor)  
  - Role: Editor extensions for Scene State assets using Motion Design components.

## 3. Important Types & APIs

### `UAvaSceneStateComponent` (USceneStateComponent)

- Role: Scene State component subclass that swaps in Motion Design-specific behavior; used as the default component for Scene State actors in this integration.

### `UAvaSceneStatePlayer` (USceneStateComponentPlayer)

- Role: Scene State player implementation tailored for Motion Design playback.

### Editor extensions

- Editor code hooks Scene State editors via `UAssetEditorSubsystem` to work with the Avalanche-aware components and players.

## 4. Typical usage patterns

- Enable alongside Motion Design when using Scene State actors that should leverage Motion Design playback.
- Scene State actors automatically get `UAvaSceneStateComponent`/`UAvaSceneStatePlayer` defaults via the plugin.
- Edit Scene State assets in the editor; the plugin’s editor module ensures the Avalanche components are recognized and editable.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
