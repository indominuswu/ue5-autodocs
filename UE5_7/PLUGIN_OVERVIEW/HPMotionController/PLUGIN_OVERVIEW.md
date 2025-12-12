# HP Motion Controller Plugin Overview

## 1. What this plugin does
- Adds controller mappings for the HP Reverb G2 motion controllers in OpenXR and SteamVR.
- Supplies a runtime module that registers the device profile and input layout.
- No editor UI; activates automatically when targeting supported VR runtimes.

## 2. Editor/Runtime surfaces

- User-facing: Yes - VR projects enable this to get correct HP Reverb G2 controller mappings in OpenXR/SteamVR without extra setup.

## 3. Key Modules
- **HPMotionController** (Runtime)  
  - Role: Registers HP-specific motion controller profiles/mappings for OpenXR/SteamVR.

## 4. Important Types & APIs
- The module exposes no public UObject types; mapping logic is contained in the module implementation.

## 5. Typical usage patterns
- Enable the plugin for VR projects using HP Reverb G2 controllers; ensure OpenXR or SteamVR is active.
- Input actions/axes bound to generic motion controller keys will pick up the HP mapping automatically.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

