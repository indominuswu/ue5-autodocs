# Static Mesh Editor Modeling Mode Plugin Overview

## 1. What this plugin does
- Adds a Modeling tab/mode to the Static Mesh Editor, leveraging the Modeling Tools framework.
- Provides editor commands and toolkit wiring to expose modeling tools directly on static mesh assets.
- Bundles modeling-specific UI for static mesh contexts (requires MeshLODToolset/ModelingToolsEditorMode).

## 2. Key Modules
- **StaticMeshEditorModeling** (Editor)  
  - Role: Registers the modeling mode for the Static Mesh Editor, commands, and toolkit.  
  - Notable types: `FStaticMeshEditorModelingMode`, `FStaticMeshEditorModelingToolkit`, `FStaticMeshEditorModelingCommands`.

## 3. Important Types & APIs
### `FStaticMeshEditorModelingMode`
- Role: Mode entry that integrates modeling tools into the Static Mesh Editor.
- Key behaviors: registers tools/actions available in the modeling tab, ties into modeling tool registries.

### `FStaticMeshEditorModelingToolkit`
- Role: Toolkit that builds the UI for the modeling tab, exposing tool palettes and settings.

## 4. Typical usage patterns
- Open a static mesh asset; switch to the Modeling tab to access modeling tools (selection, remesh, deform, UV, etc.).
- Commands defined in `FStaticMeshEditorModelingCommands` provide shortcuts to commonly used modeling tools within the editor context.

## 5. Version-specific notes (UE 5.7)
- Marked beta and Win64-only; no additional UE 5.7-specific notes noted in source.
