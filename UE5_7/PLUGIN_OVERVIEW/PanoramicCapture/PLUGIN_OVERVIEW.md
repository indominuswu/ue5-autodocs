# Panoramic Capture Plugin Overview

## 1. What this plugin does

- Captures sequences of panoramic images (mono or stereo top/bottom) from the editor or runtime.
- Provides capture actors/components and utilities to drive 360° rendering workflows.

## 2. Key Modules

- **PanoramicCapture** (UncookedOnly)  
  - Role: Capture logic and helper types for panoramic output.

## 3. Important Types & APIs

- `AStereoCapturePawn` (`StereoCapturePawn.h`)  
  - Pawn set up to perform stereo panoramic captures.
- `FStereoPanorama` (`StereoPanorama.h`)  
  - High-level capture control/parameters for panorama generation.
- `FStereoPanoramaManager`, `FSceneCapturer`  
  - Manage capture sequences, cube face rendering, stitching, and output file writing.
- `UStereoStaticMeshComponent`  
  - Specialized mesh component used during capture rendering.

## 4. Typical usage patterns

- Enable the plugin, place `StereoCapturePawn` in a level, and configure capture parameters (mono/stereo, resolution, path).
- Trigger captures via Blueprints or editor commands; outputs panoramic image sequences suitable for 360 viewers or stitching workflows.
- Designed for offline capture; no dedicated UI beyond pawn properties and console/Blueprint controls.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview reflects the current panoramic capture implementation in the UE 5.7 source tree.
