# Chaos Solver Plugin Overview

## 1. What this plugin does

- Adds editor tooling for working with Chaos physics solver assets and actors.
- Provides factories and asset type actions to create and place Chaos Solver actors in levels.
- Supplies details customizations and styling for solver-centric workflows.

## 2. Key Modules

- **ChaosSolverEditor** (Editor)  
  - Role: Editor-only utilities, factories, and details customizations for Chaos Solver assets/actors.
  - Notable types: `UChaosSolverFactory`, `UActorFactoryChaosSolver`, `FAssetTypeActions_ChaosSolver`, `FChaosSolverEditorCommands`.

## 3. Important Types & APIs

### `UChaosSolverFactory` and `UActorFactoryChaosSolver`
- Role: Create Chaos Solver assets and place solver actors in levels from the editor content browser/placement tools.

### `FAssetTypeActions_ChaosSolver`
- Role: Registers the Chaos Solver asset type, thumbnail, and menu actions.

### `FChaosSolverEditorDetails` and `FChaosSolverEditorStyle`
- Role: Details panel customization and styling for solver editing sessions.

## 4. Typical usage patterns

- Enable the plugin to expose Chaos Solver asset/actor creation in the editor.
- Use the asset factory or placement tools to create solver actors, then configure solver parameters via the customized details panel.
- Leverage registered asset actions for duplication, editing, and organization of solver assets.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
