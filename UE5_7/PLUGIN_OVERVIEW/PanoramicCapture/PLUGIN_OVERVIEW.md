# Panoramic Capture Plugin Overview

## 1. What this plugin does

- Captures sequences of panoramic images (mono or stereo top/bottom) from the editor or runtime.
- Provides capture actors/components and utilities to drive 360-degree rendering workflows.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Exposes `AStereoCapturePawn`/panorama helpers that users place or script to capture mono/stereo 360 imagery from their scenes.

## 3. Key Modules

- **PanoramicCapture** (UncookedOnly)  
  - Role: Capture logic and helper types for panoramic output.

## 4. Important Types & APIs

- `AStereoCapturePawn` (`StereoCapturePawn.h`)  
  - Pawn set up to perform stereo panoramic captures.
- `FStereoPanorama` (`StereoPanorama.h`)  
  - High-level capture control/parameters for panorama generation.
- `FStereoPanoramaManager`, `FSceneCapturer`  
  - Manage capture sequences, cube face rendering, stitching, and output file writing.
- `UStereoStaticMeshComponent`  
  - Specialized mesh component used during capture rendering.

## 5. Typical usage patterns

- Enable the plugin, place `StereoCapturePawn` in a level, and configure capture parameters (mono/stereo, resolution, path).
- Trigger captures via Blueprints or editor commands; outputs panoramic image sequences suitable for 360 viewers or stitching workflows.
- Designed for offline capture; no dedicated UI beyond pawn properties and console/Blueprint controls.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview reflects the current panoramic capture implementation in the UE 5.7 source tree.



