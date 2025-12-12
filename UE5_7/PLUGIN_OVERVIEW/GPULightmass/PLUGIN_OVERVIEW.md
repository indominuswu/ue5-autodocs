# GPU Lightmass Plugin Overview

## 1. What this plugin does
- Provides a DXR-backed GPU light baking and interactive preview path for static lighting.
- Enables “Bake What You See” workflows and denoised previews for lightmaps and volumetric lightmaps.
- Integrates an editor UI and settings asset for controlling GPU Lightmass quality and behavior.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor panel/settings (`UGPULightmassSettings`) let users run GPU Lightmass bakes (Full or Bake What You See) and tune bake quality/denoiser options.

## 3. Key Modules
- **GPULightmass** (UncookedOnly)  
  - Role: Core GPU Lightmass renderer, ray tracing/lightmap generation, denoising, and tile management.
- **GPULightmassEditor** (Editor)  
  - Role: Editor integration for starting/stopping GPU bakes, exposing settings, and viewport UI.

## 4. Important Types & APIs

### `UGPULightmassSettings`
- Role: UObject-based settings for GPU Lightmass; configurable in-editor and BlueprintType.
- Key properties: `Mode` (FullBake vs BakeWhatYouSee), `DenoisingOptions`/`Denoiser`, `GISamples`, `StationaryLightShadowSamples`, `bUseIrradianceCaching`, `VolumetricLightmapQualityMultiplier`, `FirstBounceRayGuiding` options, leak prevention toggles, and progress visualization flags.

## 5. Typical usage patterns
- Enable the plugin (experimental) and open the GPU Lightmass UI in the editor; choose Full Bake or Bake What You See.
- Tune `UGPULightmassSettings` (exposed via the GPU Lightmass panel/world settings) for sample counts, denoiser usage, irradiance caching, and volumetric lightmap quality.
- Trigger a bake to generate lightmaps via GPU/DXR; use interactive preview to validate results before saving.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

