# OpenColorIO (OCIO) Plugin Overview

## 1. What this plugin does
- Integrates OpenColorIO color management for converting, baking, and applying color spaces in rendering and compositing pipelines.
- Provides configuration assets that describe color spaces, displays, and views, plus runtime helpers to apply OCIO transforms to textures and viewports.
- Adds editor tooling for authoring OCIO configuration assets, detail customizations, and Blueprint utilities for baking transforms into textures.
- Supplies a display extension to apply OCIO transforms in editor or in-game viewports.

## 2. Key Modules
- **OpenColorIO** (Runtime)  
  - Role: Core OCIO asset types, shader/LUT generation, runtime rendering helpers, Blueprint library, display extension support.  
  - Notable types: `UOpenColorIOConfiguration`, `UOpenColorIOColorTransform`, `UOpenColorIOBlueprintLibrary`, `UOpenColorIODisplayExtensionWrapper`, `UOpenColorIOSettings`.
- **OpenColorIOEditor** (Editor)  
  - Role: Asset factories, editor detail customizations, viewport display controls, Blueprint helpers for baking textures.  
  - Notable types: `UOpenColorIOEditorBlueprintLibrary`, `UOpenColorIODefaultViewportSettings`, `UOpenColorIOLevelViewportSettings`, asset definitions/factories for OCIO configuration assets.

## 3. Important Types & APIs
### `UOpenColorIOConfiguration`
- Role: Asset describing available OCIO color spaces, displays, and views; drives transform creation.
- Key properties: references to configuration file; color space/display/view entries; cache of baked transforms.

### `UOpenColorIOColorTransform`
- Role: Generates shader resources and LUT textures for a specific color space/view transform and exposes helpers to transform colors or images.
- Key functions: `Initialize(...)`, `GetRenderResources(...)`, `TransformColor`, `TransformImage`, `GetTransformProcessor`, `CacheResourceShadersForRendering`.

### `UOpenColorIOBlueprintLibrary`
- Role: Blueprint callable helpers to apply OCIO color-space transforms at runtime.
- Key functions: `ApplyColorSpaceTransform(...)` operating on textures and render targets.

### `UOpenColorIODisplayExtensionWrapper`
- Role: Blueprint-manageable wrapper around the scene view extension that applies OCIO display transforms to viewports.
- Key functions: `CreateOpenColorIODisplayExtension`, `CreateInGameOpenColorIODisplayExtension`, `SetOpenColorIOConfiguration`, `RemoveSceneExtension`.

### `UOpenColorIOSettings`
- Role: Developer settings controlling OCIO behavior (legacy processor toggle, 32f LUTs, shader compilation options).

### `UOpenColorIOEditorBlueprintLibrary`
- Role: Editor-only Blueprint functions to bake OCIO transforms into textures (compressed or uncompressed).

## 4. Typical usage patterns
- Editor: Create an `OpenColorIOConfiguration` asset via the OCIO configuration factory, set source configuration/displays/views, and assign default viewport settings in project settings. Use editor Blueprint nodes to bake transforms into textures.
- Runtime: Add an `OpenColorIODisplayExtensionWrapper` in Blueprint or C++ and set display configuration to apply OCIO display transforms to viewports. Use `UOpenColorIOBlueprintLibrary::ApplyColorSpaceTransform` to convert textures to a target space or display/view.
- Rendering: Use OCIO configuration to generate LUTs/shaders; the display manager tracks per-viewport configurations for preview.

## 5. Version-specific notes (UE 5.7)
- Marked as beta in the plugin descriptor; several APIs include 5.6 deprecation notices but no UE 5.7-specific flags were found.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
