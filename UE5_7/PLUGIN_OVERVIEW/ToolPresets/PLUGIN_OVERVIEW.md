# Tool Presets Plugin Overview

## 1. What this plugin does

- Adds editor support for saving/loading Interactive Tools Framework settings as reusable presets.
- Maintains a default preset collection asset and exposes a UI to manage presets.
- Enabled by default in the editor category.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor UI and subsystem for creating and applying Interactive Tools Framework presets.

## 3. Key Modules

- **ToolPresetAsset** (Editor)
  - Role: Defines preset asset types and an editor subsystem to manage the default collection.
- **ToolPresetEditor** (Editor)
  - Role: Provides Slate UI (`SToolPresetManager`), styles, and settings for preset authoring.

## 4. Important Types & APIs

### `UInteractiveToolsPresetCollectionAsset`

- Role: Asset that stores tool preset entries (referenced by the subsystem).

### `UToolPresetAssetSubsystem`

- Role: Editor subsystem ensuring a default preset collection exists; exposes `GetDefaultCollection` and `SaveDefaultCollection` helpers.

### `UToolPresetSettings`

- Role: Editor settings object controlling preset behavior and defaults.

### `SToolPresetManager`

- Role: Slate panel to browse, save, and apply presets across tools.

## 5. Typical usage patterns

- Enable the plugin (enabled by default), open the Tool Preset manager UI, and save tool configurations into the default collection.
- Use the editor subsystem to persist or retrieve the default preset asset for distribution to teams.
- Apply presets to restore preferred tool settings quickly across sessions.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
