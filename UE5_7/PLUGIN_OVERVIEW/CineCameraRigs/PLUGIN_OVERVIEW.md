# CineCameraRigs Plugin Overview

## 1. What this plugin does

- Adds spline-based cinematic camera rigs for virtual production workflows.
- Extends spline components with camera-specific metadata (focal length, aperture, focus distance, rotation).
- Provides editor visualizers and settings for authoring camera splines.

## 2. Key Modules

- **CineCameraRigs** (Runtime)  
  - Role: Runtime components and data structures for camera splines and metadata.
  - Notable types: `UCineSplineComponent`, `UCineSplineMetadata`, `FCineSplinePointData`, `FCineSplineCurveDefaults`.
- **CineCameraRigsEditor** (Editor)  
  - Role: Editor visualizers, settings, and customization for camera rigs.
  - Notable types: `UCineCameraRigsSettings`, `FCineSplineComponentVisualizer`.

## 3. Important Types & APIs

### `UCineSplineComponent`
- Role: Spline component specialized for cinematic camera paths; stores per-point camera metadata.
- Key functions: Set per-point focal length, aperture, focus distance, custom position, and rotation; metadata retrieval via overridden spline metadata accessors.
- Data: Holds `UCineSplineMetadata` and default curve settings to propagate to points.

### `UCineSplineMetadata` / `FCineSplinePointData`
- Role: Store camera properties along the spline (focal length, aperture, focus distance, transforms).

### `UCineCameraRigsSettings`
- Role: Editor settings controlling defaults/behavior for camera rig authoring.

## 4. Typical usage patterns

- Enable the plugin and add a `UCineSplineComponent` to actors representing camera paths.
- Author spline points and set camera metadata per point (focal length, aperture, focus distance, rotations) via Blueprint or details panel.
- Use the editor visualizer to adjust and preview camera paths; metadata is applied during runtime camera evaluation/rendering.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
