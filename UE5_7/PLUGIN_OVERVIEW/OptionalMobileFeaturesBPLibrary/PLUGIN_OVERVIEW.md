# Optional Mobile Features Blueprint Library Plugin Overview

## 1. What this plugin does

- Exposes optional mobile device features (sound volume, battery charge level, system temperature) to Blueprints on Android and iOS.
- Provides a lightweight runtime Blueprint library without additional editor tooling.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime Blueprint library exposing mobile device info; no editor tooling.

## 3. Key Modules

- **OptionalMobileFeaturesBPLibrary** (Runtime)  
  - Role: Blueprint-facing API that queries platform-specific device info.

## 4. Important Types & APIs

- `UOptionalMobileFeaturesBPLibrary` (`OptionalMobileFeaturesBPLibrary.h`)  
  - Blueprint-callable functions for retrieving battery level, temperature state, and sound volume.
- `FOptionalMobileFeaturesBPLibraryModule`  
  - Module bootstrap; ensures the library is registered for Blueprint use.

## 5. Typical usage patterns

- Enable the plugin for mobile projects; call the Blueprint nodes from gameplay/UI Blueprints to display device status or adjust behavior based on thermal/volume state.
- No assets or editor UI are added; usage is entirely via Blueprint nodes or equivalent C++ calls.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
