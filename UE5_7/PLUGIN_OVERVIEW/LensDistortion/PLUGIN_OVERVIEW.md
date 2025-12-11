# Lens Distortion (Deprecated) Plugin Overview

## 1. What this plugin does
- Provides legacy Blueprint utilities for rendering lens distortion/undistortion displacement maps.
- Exposes helpers for calculating overscan required to avoid clipping distorted pixels.
- Marked deprecated in favor of the CameraCalibration/LensComponent workflow.

## 2. Key Modules
- **LensDistortion** (Runtime)  
  - Role: Legacy distortion math and Blueprint library for generating UV displacement and overscan factors.
  - Notable types: `ULensDistortionBlueprintLibrary`, `FLensDistortionCameraModel`.

## 3. Important Types & APIs

### `ULensDistortionBlueprintLibrary`
- Role: Blueprint function library for computing distortion/undistortion data.
- Key functions: `GetUndistortOverscanFactor` (calculates overscan), `DrawUVDisplacementToRenderTarget` (writes distortion/undistortion displacement to a render target), equality/inequality checks for `FLensDistortionCameraModel`.
- All functions are flagged deprecated with guidance to migrate.

## 4. Typical usage patterns
- Existing projects may still call the Blueprint library to render distortion maps or compute overscan from an `FLensDistortionCameraModel`.
- New projects should switch to the CameraCalibration plugin with `ULensComponent` and lens files; this plugin is retained only for backward compatibility.

## 5. Version-specific notes (UE 5.7)
- Plugin description explicitly warns of deprecation and future removal; no UE 5.7-only features beyond the deprecation notice.

