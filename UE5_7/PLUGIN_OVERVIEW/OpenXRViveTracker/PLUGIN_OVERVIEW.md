# OpenXR Vive Tracker Plugin Overview

## 1. What this plugin does

- Adds support for the `XR_HTCX_vive_tracker_interaction` OpenXR extension to use Vive/HTC trackers through OpenXR.
- Registers tracker devices so they appear as tracked poses/inputs inside Unreal’s XR framework.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Registers the Vive tracker interaction profile so developers can read tracker poses/inputs via the usual OpenXR motion-controller APIs.

## 3. Key Modules

- **OpenXRViveTracker** (Runtime)  
  - Role: Registers the Vive tracker interaction profile and surfaces tracker poses/inputs to the engine.

## 4. Important Types & APIs

- `FOpenXRViveTracker` (`OpenXRViveTracker.h`)  
  - Implements tracker discovery, pose updates, and OpenXR action binding for trackers.
- `IOpenXRViveTrackerModule`  
  - Module interface to check availability and manage registration.

## 5. Typical usage patterns

- Enable alongside the OpenXR plugin when targeting OpenXR runtimes with Vive tracker support.
- Use standard XR tracking/motion controller APIs to read tracker transforms or inputs once the profile is active.
- No dedicated editor UI; configuration is via OpenXR project settings and controller mappings.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current Vive tracker integration in the UE 5.7 source tree.

