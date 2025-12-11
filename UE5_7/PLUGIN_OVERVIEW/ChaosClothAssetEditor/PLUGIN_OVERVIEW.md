# Chaos Cloth Asset Editor Plugin Overview

## 1. What this plugin does

- Provides editor tooling for authoring and modifying Chaos cloth assets.
- Adds Dataflow nodes, viewport/editor modes, and UI subsystems tailored for cloth asset editing.
- Includes tooling modules for cloth asset utilities and dataflow-driven workflows.

## 2. Key Modules

- **ChaosClothAssetEditor** (Editor)  
  - Role: Core cloth asset editor toolkit, viewport, and visualization.
- **ChaosClothAssetEditorTools** (Editor)  
  - Role: Tool implementations (e.g., weight map painting, skin weight transfer) used inside the editor.
- **ChaosClothAssetDataflowNodes** (Editor)  
  - Role: Dataflow nodes specific to cloth asset processing/import.
- **ChaosClothAssetTools** (UncookedOnly)  
  - Role: Additional uncooked-only utilities leveraged by the editor workflow.

## 3. Important Types & APIs

- `UChaosClothAssetEditorUISubsystem` / `UAssetEditorUISubsystem` integration  
  - Role: UI subsystem for cloth asset editor mode and panels.
- `UChaosClothComponent` usage across preview/viewport clients  
  - Role: Component used for simulating/previewing cloth assets in the editor viewport.
- `UClothEditorMode`, `UClothEditorToolkit`, `UClothEditor3DViewportClient` (ChaosClothAssetEditor module)  
  - Role: Editor mode and toolkit controlling viewport interaction and visualization.
- Tool classes like `UClothWeightMapPaintTool`, `UClothTransferSkinWeightsTool` (ChaosClothAssetEditorTools module)  
  - Role: Provide interactive editing tools for cloth weights and skinning.
- Dataflow nodes such as `UDatasmithImportNode` (ChaosClothAssetDataflowNodes)  
  - Role: Dataflow processors for importing/processing cloth data.

## 4. Typical usage patterns

- Enable alongside Chaos Cloth Asset to edit cloth assets within the dedicated cloth asset editor mode.
- Use viewport tools (paint weights, transfer skin weights) to refine cloth behavior and bindings.
- Employ Dataflow nodes when importing or processing cloth meshes for Chaos simulation.
- Preview cloth with `UChaosClothComponent` in the editor viewport to validate simulation responses.

## 5. Version-specific notes (UE 5.7)

- Editor-only plugin (some uncooked-only tools) and disabled by default in this 5.7 tree.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
