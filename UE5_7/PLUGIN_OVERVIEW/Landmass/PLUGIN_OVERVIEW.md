# Landmass Plugin Overview

## 1. What this plugin does

- Experimental landscape authoring toolkit that uses blueprintable brush actors to sculpt and texture landscapes procedurally.
- Provides blueprint brushes, erosion brushes, and managers that integrate with `LandscapeBlueprintBrushBase`.
- Ships with both runtime and editor modules; content-enabled for preview materials and meshes.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor landscape brush actors/blueprint utilities and runtime support for Landmass brushes.

## 3. Key Modules

- **Landmass** (Runtime, Default) — Core runtime types for Landmass actors/brushes.
- **LandmassEditor** (Editor, Default) — Editor tools, blueprint libraries, and UI integration.

## 4. Important Types & APIs

### `ALandmassActor` (AActor, editor-only brush)

- Role: Blueprintable landscape brush actor that renders into landscape height/weight maps.
- Key properties: brush size, affects height/weight/visibility, blend modes, height/weight materials, layer ordering controls, preview/selection handlers.
- Functions: `RenderLayer`, `FastPreviewMode`, `RestoreLandscapeEditing`, move brush up/down/top/bottom, update brush extents, editor tick toggles.

### `ALandmassManagerBase` (AActor)

- Role: Manager actor referenced by brushes to coordinate updates and layer ordering.

### `ALandmassErosionBrushBase` (AActor)

- Role: Blueprintable base for erosion-style brushes (extends landscape brush workflow).

### `ULandmassBlueprintFunctionLibrary`

- Role: Editor blueprint helpers under the Landmass namespace for working with brushes and manager utilities.

## 5. Typical usage patterns

- Enable the plugin (experimental). Place `ALandmassActor` instances in the level; assign materials and blend modes to sculpt heightmaps/weightmaps.
- Use layer ordering functions (MoveUp/Down/Top/Bottom) to control brush stacking; toggle fast preview mode for responsive editing.
- Extend `ALandmassErosionBrushBase` or create derived blueprint brushes for custom height/weight effects; connect them to a manager if required.

## 6. Version-specific notes (UE 5.7)

- Marked beta/experimental; no additional UE 5.7-specific behaviors identified in the source.
