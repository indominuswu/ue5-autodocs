# Geometry Mask Plugin Overview

## 1. What this plugin does

- Provides a virtual production-oriented system for writing and reading mask data to world-aligned canvases via components.
- Offers a world subsystem and canvas assets/resources for managing mask textures and post-process outputs (blur, distance field).
- Includes editor UI to browse canvases/resources and preview mask output.

## 2. Key Modules

- **GeometryMask** (Runtime)  
  - Role: Runtime mask canvas management, read/write components, post-process shaders, and subsystem support.  
  - Notable types: `UGeometryMaskCanvas`, `AGeometryMaskCanvasActor`, `UGeometryMaskCanvasResource`, `UGeometryMaskWriteComponent`, `UGeometryMaskReadComponent`, `UGeometryMaskSubsystem`, `UGeometryMaskWorldSubsystem`, `UGeometryMaskSettings`, shader helpers (`FGeometryMaskPostProcess_Blur`, `FGeometryMaskPostProcess_DistanceField`), interfaces `IGeometryMaskReadInterface` / `IGeometryMaskWriteInterface`.

- **GeometryMaskEditor** (Editor)  
  - Role: Editor widgets and view models for inspecting canvases/resources and previewing masks.  
  - Notable types: `FGeometryMaskEditorModule`, view models (`FGMECanvasListViewModel`, `FGMEResourceListViewModel`) and widgets (`SGMECanvasList`, `SGMEResourceList`, `SGeometryMaskCanvasPreview`).

## 3. Important Types & APIs

### `UGeometryMaskCanvas` / `UGeometryMaskCanvasResource`

- Role: Define mask surfaces and backing resources that read/write components operate on.
- Key properties: Resolution, format, associated world resource handles.

### `UGeometryMaskWriteComponent` / `UGeometryMaskReadComponent`

- Role: Actor components that respectively write mask values (from geometry or scripted input) and sample mask data.
- Key properties: Target canvas/resource references, write parameters, read sampling options.

### `UGeometryMaskSubsystem` / `UGeometryMaskWorldSubsystem`

- Role: Manage canvas lifecycles and provide world-level access to mask resources and global settings.

### Post-process shaders

- Role: Optional blur/distance-field passes (`GeometryMaskPostProcess_*`) to post-process mask outputs.

## 4. Typical usage patterns

- Enable the plugin, create or place an `AGeometryMaskCanvasActor`, and configure its canvas settings.
- Add `UGeometryMaskWriteComponent` to actors that should project/write into the canvas; add `UGeometryMaskReadComponent` to consumers that need to sample mask data.
- Adjust runtime settings via `UGeometryMaskSettings` and world subsystem; enable blur/distance-field passes if needed.
- In the editor, use the Geometry Mask browser widgets to inspect canvases/resources and view the preview widget for debugging.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
