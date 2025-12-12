# XRVisualization Plugin Overview

## 1. What this plugin does
- Provides a lightweight visualization helper for XR devices (HMDs, motion controllers, hand tracking) via Blueprint.
- Supplies meshes for common devices and draws them even on systems lacking native models.
- Depends on XRBase data structures and ProceduralMeshComponent for rendering support.
- Disabled by default; aimed at debugging or generic visualization.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Exposes Blueprint nodes to render XR device visualizations at runtime for debugging or simulation.

## 3. Key Modules
- **XRVisualization** (Runtime): Contains the Blueprint library and mesh loading helpers.

## 4. Important Types & APIs
- `UXRVisualizationFunctionLibrary` (BlueprintFunctionLibrary):
  - `RenderHMD(const FXRHMDData&)`: Render a generic HMD visualization.
  - `RenderMotionController2(const FXRMotionControllerState&)`: Draw a controller model for tracked controllers.
  - `RenderHandTracking(const FXRHandTrackingState&)`: Visualize tracked hands.
  - Internally ensures meshes are loaded via `UXRVisualizationLoadHelper` and issues rendering calls.
- `UXRVisualizationLoadHelper`: UObject that caches generic HMD/controller meshes (Oculus, Vive, STEM, generic).

## 5. Typical usage patterns
- Enable the plugin and call the Blueprint nodes from gameplay or debugging scripts to visualize XR devices.
- Pass XR device data obtained from `UHeadMountedDisplayFunctionLibrary` or other XRBase queries into the visualization functions.
- Suitable for tooling/simulation scenarios where native device models are unavailable.

## 6. Version-specific notes (UE 5.7)
- Plugin is marked beta and disabled by default; no additional UE 5.7-specific behaviors noted.
