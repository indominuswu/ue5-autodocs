# Landscape Patch Plugin Overview

## 1. What this plugin does

- Adds landscape patch components that can be attached to actors/meshes to affect landscape height and weightmaps procedurally.
- Supports texture-backed patches, circle/shape patches, and bindable edit layers for ordered blending.
- Provides runtime components plus editor-only tooling; includes compatibility manager for legacy patch actors.

## 2. Key Modules

- **LandscapePatch** (Runtime, PostConfigInit) — Core patch components, edit layers, and render target utilities.
- **LandscapePatchEditorOnly** (Editor, PostEngineInit) — Editor integrations and details/UI support.

## 3. Important Types & APIs

### `ULandscapePatchComponent` (USceneComponent)

- Role: Base component for patches that render into landscape edit layers; controls priorities and binding to `ULandscapePatchEditLayer`.
- Key features: priority, edit-layer binding, lifecycle hooks for render targets.

### `ULandscapePatchEditLayer` (ULandscapeEditLayerProcedural)

- Role: Maintains the list/order of registered `ULandscapePatchComponent` instances and applies them to a landscape edit layer.
- Manages patch ordering, registration, and invalid patch cleanup.

### `ULandscapeTexturePatch` (ULandscapePatchComponent)

- Role: Texture-driven patch supporting height and weightmap painting via render targets.
- Helpers: `ULandscapeWeightPatchTextureInfo`, `ULandscapeHeightTextureBackedRenderTarget`, `ULandscapeWeightTextureBackedRenderTarget` for managing internal textures.

### `ULandscapeCircleHeightPatch` (ULandscapePatchComponent)

- Role: Simple circular height patch implementation using the patch component base and edit-layer renderer interface.

### `ULandscapePatchManager` (deprecated)

- Role: Legacy actor for patch aggregation; kept for backward compatibility but superseded by `ULandscapePatchEditLayer`.

## 4. Typical usage patterns

- Enable the plugin. Add `ULandscapePatchComponent`-derived components (e.g., `LandscapeTexturePatch` or `LandscapeCircleHeightPatch`) to actors and bind them to a landscape’s procedural edit layer.
- Configure render targets, weight/height materials, and priorities; patches update the landscape when moved or when their render targets change.
- Use the edit-layer binding to order multiple patches; the editor module provides details UI for managing registered patches.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes; deprecated `ULandscapePatchManager` remains for compatibility while new edit-layer workflow is active.

