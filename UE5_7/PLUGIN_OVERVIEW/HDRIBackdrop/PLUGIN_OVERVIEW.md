# HDRIBackdrop Plugin Overview

## 1. What this plugin does
- Provides an editor placement entry for an HDRI Backdrop Blueprint used for environment lighting/backgrounds.
- Registers styling and placement category integration so the backdrop can be dragged into a level from Place Mode.
- Relies on packaged content (`/HDRIBackdrop/Blueprints/HDRIBackdrop`) for the actual actor implementation.

## 2. Key Modules
- **HDRIBackdrop** (Editor)  
  - Role: Minimal editor module that registers placement items and Slate style for the HDRI Backdrop Blueprint.

## 3. Important Types & APIs

### Module helpers
- `FHDRIBackdropModule`: Startup/shutdown for the plugin.
- `FHDRIBackdropPlacement`: Registers the HDRI Backdrop Blueprint with the Placement Mode (Lights category).
- `FHDRIBackdropStyle`: Provides Slate styles/icons for the placement UI.

## 4. Typical usage patterns
- Enable the plugin; in the editor Place Mode (Lights category), drag the “HDRI Backdrop” entry to the level.
- The placed actor is the Blueprint at `/HDRIBackdrop/Blueprints/HDRIBackdrop`, which encapsulates the dome mesh/material and exposure controls.
- Adjust Blueprint-exposed parameters (intensity, rotation, texture) directly on the placed actor.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
