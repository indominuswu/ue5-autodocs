# Game Features Plugin Overview

## 1. What this plugin does
- Provides the framework for modular Game Feature plugins, including discovery, activation, and content injection at runtime.
- Supplies data assets and actions (`UGameFeatureData`, `UGameFeatureAction*`) to register components, data registries, cheats, world partition content, and more.
- Includes an editor module for managing Game Feature plugins and validation within the editor.

## 2. Key Modules
- **GameFeatures** (Runtime)
  - Role: Core runtime for Game Feature plugin lifecycle, state machines, optional content installation, and gameplay injection hooks.
  - Notable types: `UGameFeaturesSubsystem`, `UGameFeatureData`, `UGameFeatureAction` family, `UGameFeaturesProjectPolicies`, `UGameFeatureStateChangeObserver`, `UGameFeaturePluginOperationResult`, `UGameFeatureOptionalContentInstaller`.
- **GameFeaturesEditor** (Editor)
  - Role: Editor tooling for authoring Game Feature plugins, verification, and commandlets (e.g., verse path mapper).
  - Notable types: `UGameFeaturePluginOperationResult` (shared), `UGameFeatureVersePathMapperCommandlet`, editor policy helpers.

## 3. Important Types & APIs

### `UGameFeaturesSubsystem`
- Role: Engine subsystem managing discovery, install, load, and activation of Game Feature plugins.
- Key functions: Start/stop change requests, query plugin states, trigger activation for `UGameFeatureData` assets; configured via `UGameFeaturesSubsystemSettings`.

### `UGameFeatureData`
- Role: Primary data asset describing a Game Feature plugin.
- Key properties: Array of `UGameFeatureAction` entries (e.g., `UGameFeatureAction_AddComponents`, `UGameFeatureAction_AddWorldPartitionContent`, `UGameFeatureAction_AddDataRegistrySource`, `UGameFeatureAction_AddCheats`, `UGameFeatureAction_AddActorFactory`) and plugin-wide metadata.

### `UGameFeatureAction` subclasses
- Role: Execute specific injectors when a Game Feature activates.
- Examples: Add world partition content, register data registries, attach components to actors, register audio hooks, override chunk installs.

### `UGameFeaturesProjectPolicies`
- Role: Project-level policy hooks controlling where plugins are located, how they are mounted, and what content installation is allowed.

### `UGameFeatureStateChangeObserver`
- Role: Observer interface to receive callbacks when Game Feature plugins transition states.

## 4. Typical usage patterns
- Enable the plugin and create Game Feature plugins from the editor. Author a `UGameFeatureData` asset inside each Game Feature to declare actions and metadata.
- In code or Blueprints, request activation through `UGameFeaturesSubsystem`, which loads/mounts the plugin and executes configured actions.
- Use actions like `UGameFeatureAction_AddComponents` to inject components onto actors (via tags/filters) or `UGameFeatureAction_AddWorldPartitionContent` to stream feature-specific content.
- For projects with downloadable content, use `UGameFeatureOptionalContentInstaller` and chunk override actions to manage installs.

## 5. Version-specific notes (UE 5.7)
- Plugin marked beta in 5.7; no additional 5.7-only APIs noted. Actions and subsystem types are based on the 5.7 source tree.
