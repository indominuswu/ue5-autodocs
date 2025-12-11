# Composite Plane Plugin Overview

## 1. What this plugin does
- Provides a cine-camera-aligned composite plane actor for projecting textures or video into a scene.
- Includes placement utilities for aligning the plane relative to cameras for in-camera VFX or virtual production.

## 2. Key Modules
- **CompositePlane** (Editor)  
  - Role: Module entry that registers the composite plane actor/placement helpers for editor use.

## 3. Important Types & APIs

### `FCompositePlaneModule`
- Role: Module that starts/shuts down the composite plane tools.

### Placement helpers
- `FCompositePlanePlacement`: Utility for spawning/positioning the plane relative to a camera. (Implementation in `CompositePlanePlacement.cpp`.)

## 4. Typical usage patterns
- Editor: Enable the plugin, then add the composite plane actor through placement utilities to project reference plates or video near a cine camera.
- Runtime: The actor behaves as a textured plane aligned to camera framing; tweak transforms/materials per shot.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific behavior is explicitly noted; plugin is minimal and editor-focused.

