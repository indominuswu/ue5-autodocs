# Editor DataflowGraph Plugin Overview

## 1. What this plugin does

- Implements the Dataflow graph system used for procedural and geometry-processing pipelines.
- Provides editor tooling to author Dataflow assets, preview results, and render node outputs.
- Includes runtime nodes and engine integration to execute Dataflow graphs outside the editor.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Offers an editor mode/UI for Dataflow assets plus runtime nodes/engine integration to execute graphs.

## 3. Key Modules

- **DataflowEditor** (Editor)  
  - Role: Editor mode, UI, rendering helpers, and customization panels for Dataflow assets.
  - Notable types: `FDataflowEditorModeUILayer`, rendering utilities in `DataflowRenderableType*`.
- **DataflowAssetTools** (Runtime)  
  - Role: Asset utilities and helpers for Dataflow assets (color schemes, collection rendering patterns).
- **DataflowEnginePlugin** (Runtime)  
  - Role: Engine bridge to evaluate Dataflow graphs and scene proxies.
- **DataflowNodes** (Runtime)  
  - Role: Library of runtime Dataflow nodes and evaluators.

## 4. Important Types & APIs

### `FDataflowEditorModeUILayer`
- Role: Editor subsystem that manages the Dataflow editor mode UI.
- Key behavior: Registers UI layers and tools for authoring graphs.

### Rendering helpers (`DataflowRenderableTypeInstance`, `DataflowEngineSceneProxy`)
- Role: Provide rendering proxies for Dataflow preview meshes and hit proxies in the viewport.

### `UDataflowEditorBlueprintLibrary`
- Role: Blueprint function library for editor scripting around Dataflow assets (found in `DataflowEditorBlueprintLibrary.h`).
- Key functions: Utility calls for creating or manipulating Dataflow assets from scripts.

## 5. Typical usage patterns

- Enable the plugin to work with Dataflow assets in the editor; use the Dataflow editor mode to build node graphs.
- Author nodes using the provided node library (`DataflowNodes`) and preview results in the viewport with rendering helpers.
- Use Dataflow runtime modules to execute graphs in tools or runtime contexts that rely on Dataflow-generated data.

## 6. Version-specific notes (UE 5.7)

- Editor module is enabled by default; runtime modules ship with the experimental Dataflow system in UE 5.7. No explicit 5.7-only changes noted.
