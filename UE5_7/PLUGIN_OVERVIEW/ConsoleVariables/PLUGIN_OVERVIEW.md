# Console Variables Editor Plugin Overview

## 1. What this plugin does
- Editor panel for saving, loading, and controlling console variables (cvars) via assets and UI.
- Provides a runtime asset that stores sets of cvars and can apply them in-game.
- Includes Blueprint helpers and project settings to manage cvar presets and multi-user support.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor Console Variables panel plus `UConsoleVariablesAsset`/Blueprint library let users author and apply cvar preset assets in editor and at runtime (with multi-user support).

## 3. Key Modules
- **ConsoleVariablesEditor** (UncookedOnly)  
  - Role: Editor UI, asset actions, multi-user support, and styles for the Console Variables panel.
- **ConsoleVariablesEditorRuntime** (Runtime)  
  - Role: Runtime asset type and minimal runtime module for applying stored cvar sets.

## 4. Important Types & APIs

### `UConsoleVariablesAsset`
- Role: Runtime asset storing named cvar/value pairs and metadata; can be loaded/applied at runtime.

### `UConsoleVariablesEditorProjectSettings`
- Role: Project settings that configure default asset locations and editor behavior for cvar management.

### `UConsoleVariablesEditorFunctionLibrary`
- Role: Blueprint-exposed functions to load/save/apply console variable sets and interact with the editor module.

### Editor utilities
- `FConsoleVariablesEditorModule`, command infos, asset factories, and Slate views under `Views/` provide the editor panel and multi-user integration.

## 5. Typical usage patterns
- Editor: Use the Console Variables panel to capture current cvars into a `Console Variables Asset`, edit values, and save/load presets. Multi-user helpers allow sharing presets.
- Runtime: Reference a `Console Variables Asset` and apply it via `UConsoleVariablesEditorFunctionLibrary` or manual loading to set cvars at startup or during gameplay.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific behavior called out; overview reflects current runtime/editor sources.

