# ML Deformer Nearest Neighbor Model (Deprecated) Plugin Overview

## 1. What this plugin does
- Implements a nearest-neighbor ML deformer model for the ML Deformer Framework.
- Marked deprecated in the plugin description; superseded by newer models (e.g., Detail Pose Model).
- Provides runtime model classes plus editor tooling for authoring and visualization.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime deformer model plus editor integration (deprecated but still exposed to users).

## 3. Key Modules
- **NearestNeighborModel** (Runtime)  
  - Runtime evaluation of the nearest-neighbor morph-based model.  
  - Notable types: `UNearestNeighborModel` (extends `UMLDeformerMorphModel`), `UNearestNeighborModelInstance`, `UNearestNeighborModelInputInfo`, `UNearestNeighborModelVizSettings`, helper classes for optimized network loading (deprecated loader warnings present).
- **NearestNeighborModelEditor** (Editor)  
  - Editor integration for the model.  
  - Notable types: `FNearestNeighborEditorModel`, `FNearestNeighborEditorModelActor`, `UNearestNeighborEditorModel`, viz settings details, editor actors used for preview.

## 4. Important Types & APIs

### `UNearestNeighborModel`
- Role: Morph-based ML deformer model that selects nearest neighbors to drive deformations; holds training inputs (animations, geometry cache) and section weight maps.
- Key properties include section definitions (`UNearestNeighborModelSection`), weight map creation settings, and references to optimized networks.

### `UNearestNeighborModelInstance`
- Role: Runtime instance used by `UMLDeformerComponent` to evaluate the nearest-neighbor model; manages optimized network execution.

### `UNearestNeighborModelVizSettings`
- Role: Visualization settings for previewing nearest-neighbor results (geometry cache, activation colors, debug overlays).

### Editor helpers
- `UNearestNeighborModelInputInfo` for editor-side data prep, `FNearestNeighborEditorModel`/`Actor` for preview and detail customizations.

## 5. Typical usage patterns
- Enable alongside `MLDeformerFramework`; create an ML Deformer Asset using the Nearest Neighbor model type.
- Configure training data (animation sequences, geometry cache) and section weight maps; train/export the optimized network.
- Attach `UMLDeformerComponent` to a compatible skeletal mesh and use the Nearest Neighbor model asset; adjust visualization via `UNearestNeighborModelVizSettings` in the deformer editor.
- Consider migrating to a newer model per the deprecation notice.

## 6. Version-specific notes (UE 5.7)
- The plugin is explicitly marked “(DEPRECATED)” in its description and includes deprecated helpers (`UNearestNeighborOptimizedNetworkLoader` deprecated since 5.4).
- No additional UE 5.7-specific changes noted beyond the deprecation status in this source tree.
