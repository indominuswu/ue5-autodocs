# glTF Exporter Plugin Overview

## 1. What this plugin does

- Exports Unreal content to glTF 2.0 (including meshes, materials, animations, Level Sequences, and variant sets).
- Provides export options, proxy material baking, and analytics for export operations.
- Integrates with the editor to expose export dialogs, material previews, and asset actions for glTF proxy assets.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor export dialogs/options and exporter classes let users export levels/meshes/sequences to glTF with proxy material baking.

## 3. Key Modules

- **GLTFExporter** (Runtime)  
  - Role: Core export logic, converters, task builders, UI hooks, and proxy material handling.  
  - Notable types: `FGLTFExporterModule`, exporters (`FGLTFExporter`, `FGLTFLevelExporter`, `FGLTFLevelSequenceExporter`, `FGLTFAnimSequenceExporter`, `FGLTFMaterialExporter`, `FGLTFSkeletalMeshExporter`, `FGLTFStaticMeshExporter`, `FGLTFLevelVariantSetsExporter`), builders (`FGLTFBuilder`, `FGLTFConvertBuilder`, `FGLTFJsonBuilder`, `FGLTFBufferBuilder`), converters (`FGLTFMeshConverters`, `FGLTFMaterialConverters`, `FGLTFAnimationConverters`, `FGLTFNodeConverters`, `FGLTFImageConverters`, `FGLTFLightConverters`), options (`FGLTFExportOptions`, `FGLTFProxyOptions`), tasks (`FGLTFDelayed*Tasks`), utilities (`FGLTFMaterialProxyFactory`, `FGLTFMaterialUserData`), and editor UI helpers (`SGLTFExportOptionsWindow`, `SGLTFProxyOptionsWindow`, `FGLTFEditorStyle`).

## 4. Important Types & APIs

### Exporters (`FGLTFExporter`, `FGLTF*Exporter`)

- Role: High-level exporter classes for specific asset types (levels, sequences, skeletal/static meshes, animations, materials, variants).
- Key properties: Export options struct, output writer/context, analytics hooks.

### Builders and converters

- Role: Convert Unreal asset data into glTF JSON/binary representations; builders orchestrate buffers, images, materials, meshes, nodes, scenes, and animations.
- Key components: `FGLTFConvertBuilder`, `FGLTFJsonBuilder`, `FGLTFBufferBuilder`, converter sets for meshes/materials/animations/lights/cameras/textures.

### Options and proxy material support

- Role: `FGLTFExportOptions`/`FGLTFProxyOptions` store user-configurable settings (export selection, bake material options, image settings).
- `FGLTFMaterialProxyFactory` and related proxy utilities bake complex materials to glTF-friendly textures; `FGLTFMaterialUserData` preserves metadata on assets.

### UI and asset actions

- Role: Slate dialogs for export/proxy options, asset actions for glTF proxy assets, and analytics (`FGLTFExporterAnalytics`) for export usage.

## 5. Typical usage patterns

- Enable the plugin, select assets or a Level/Level Sequence, and trigger glTF export through the editor UI or programmatic calls to the exporter classes.
- Configure export/material bake options in the dialog; optionally generate proxy materials for glTF compatibility.
- Use variant/animation exporters when exporting sequences or Level Variant Sets; review analytics logs for automation pipelines.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

