# AnimToTexture Plugin Overview

## 1. What this plugin does
- Experimental tools to convert skeletal mesh animations into texture data for vertex animation workflows.
- Provides data assets and utilities to bake animation frames and drive playback on meshes using textures.
- Supplies editor helpers and Blueprint nodes for baking, mapping, and previewing AnimToTexture outputs.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor baking tools/Blueprint nodes plus runtime playback helpers for texture-driven animation.

## 3. Key Modules
- **AnimToTexture** (Runtime, PreDefault)
  - Role: Runtime support for reading baked data assets and applying texture-driven animation.
- **AnimToTextureEditor** (Editor, PreLoadingScreen)
  - Role: Baking utilities, asset definitions, and editor UI for generating AnimToTexture assets.

## 4. Important Types & APIs
- `UAnimToTextureDataAsset`
  - Role: Stores baked animation textures and metadata.
- `UAnimToTextureBPLibrary`
  - Role: Blueprint utilities for baking and applying AnimToTexture data.
- `FAnimToTextureMeshMapping`, `FAnimToTextureSkeletalMeshSettings`
  - Role: Mapping/parameter structures used during baking.
- `UAnimToTextureInstancePlaybackHelpers`
  - Role: Helper functions for sampling baked textures at runtime.
- Editor classes: `UAnimToTextureSkeletalMesh`, `UAnimToTextureMeshMapping`, `UAssetDefinition_AnimToTexture`
  - Role: Editor-facing asset support and configuration surfaces.

## 5. Typical usage patterns
- In the editor, use AnimToTexture tools/Blueprint nodes to bake a skeletal mesh animation sequence into textures stored in an `AnimToTextureDataAsset`.
- Apply the baked asset to meshes that support texture-driven deformation; use playback helpers to drive time sampling.
- Ideal for large crowds or effects where full skeletal evaluation is too expensive.

## 6. Version-specific notes (UE 5.7)
- Plugin is marked Experimental; no additional UE 5.7-specific notes found.
