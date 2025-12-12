# Image Plate Plugin Overview

## 1. What this plugin does
- Adds actors/components for camera-aligned image plates that can play frame sequences.
- Supports loading image file sequences and driving them as materials on in-world quads.
- Provides editor helpers for authoring and previewing image plate assets.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users create `Image Plate File Sequence` assets and place `AImagePlateActor`/`UImagePlateComponent` to play image sequences in camera-aligned plates.

## 3. Key Modules
- **ImagePlate** (Runtime)  
  - Role: Core runtime actors/components for image plates, file sequence assets, and rendering logic.
- **ImagePlateEditor** (Editor)  
  - Role: Editor integration for authoring image plate assets and placing actors.

## 4. Important Types & APIs

### Runtime
- `UImagePlateComponent`: `UPrimitiveComponent` that renders a camera-facing plate; holds sequence settings, materials, and frustum helper.
- `UImagePlateFileSequence`: Asset describing the file sequence to play (path, frame rate, range).
- `AImagePlateActor` (in module source): Actor wrapper that hosts an `ImagePlateComponent`.

## 5. Typical usage patterns
- Enable the plugin (experimental), create an `Image Plate File Sequence` asset pointing to an image sequence on disk.
- Add an `ImagePlateActor` to the level or attach an `ImagePlateComponent` to an existing actor; assign the file sequence.
- Control playback and timing through sequence settings; adjust materials/frustum to align with the camera feed.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

