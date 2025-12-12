# OpenXREyeTracker Plugin Overview

## 1. What this plugin does

- Adds support for the `XR_EXT_eye_gaze_interaction` OpenXR extension, exposing eye-tracking data to the engine.
- Provides a runtime module that implements the engine eye-tracking interface over OpenXR.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Registers an OpenXR-backed eye tracker so projects can read gaze data through UE’s eye-tracking interfaces/Blueprints when the extension is available.

## 3. Key Modules

- **OpenXREyeTracker** (Runtime)  
  - Role: Registers an eye-tracker provider backed by OpenXR and routes gaze data into UE eye-tracking APIs.

## 4. Important Types & APIs

- `IOpenXREyeTrackerModule`  
  - Module interface used to register the tracker implementation.
- `FOpenXREyeTracker` (from `OpenXREyeTracker.h`)  
  - Implements gaze tracking, validity checks, and frame updates using OpenXR eye gaze interaction.

## 5. Typical usage patterns

- Enable alongside the core OpenXR plugin and ensure the runtime supports `XR_EXT_eye_gaze_interaction`.
- Access gaze data through UE eye-tracking interfaces (C++ or Blueprint via the standard eye-tracking subsystem).
- No editor tools are provided; configuration is handled by enabling the extension in project settings/OpenXR runtime.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview reflects the OpenXR eye-tracking support in the UE 5.7 source tree.

