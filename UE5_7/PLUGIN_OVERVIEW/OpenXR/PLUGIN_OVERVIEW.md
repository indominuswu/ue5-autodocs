# OpenXR Plugin Overview

## 1. What this plugin does

- Implements OpenXR support for VR/AR headsets, input, and AR tracking through the Khronos OpenXR standard.
- Provides runtime modules for HMD rendering (`OpenXRHMD`), input binding (`OpenXRInput`), and AR features (`OpenXRAR`), plus editor tooling (`OpenXREditor`).
- Exposes Blueprint helpers and settings objects to configure OpenXR extensions and runtime behavior.

## 2. Key Modules

- **OpenXRHMD** (Runtime)  
  - Role: Core HMD integration, extension management, rendering, and session lifecycle; includes developer settings and Blueprint helpers.
- **OpenXRInput** (Runtime)  
  - Role: Input mappings, action bindings, and Enhanced Input integration; supplies Blueprint function library.
- **OpenXRAR** (Runtime)  
  - Role: AR pinning/tracking hooks for OpenXR-backed AR workflows.
- **OpenXREditor** (Editor)  
  - Role: Editor-side helpers for enabling OpenXR features and project settings UI.

## 3. Important Types & APIs

- `UOpenXRBlueprintFunctionLibrary` (HMD)  
  - Blueprint nodes for querying OpenXR instance/runtime information, extension support, and motion controller features.
- `UOpenXRInputFunctionLibrary`  
  - Blueprint access to action bindings, hand/controller state, and Enhanced Input user settings integration.
- `UOpenXRHMDSettings`  
  - DeveloperSettings-backed config for runtime features and enabled extensions.
- `IOpenXRExtensionPlugin`  
  - Interface for extension plugins to hook into rendering, tracking, and AR events.
- `FOpenXRAR` (in `OpenXRAR.h`)  
  - Handles AR pinning, spawning AR actors/components, and bridging OpenXR tracking data to AR framework types.

## 4. Typical usage patterns

- Enable the plugin and select OpenXR as the XR runtime; configure extensions in Project Settings → XR → OpenXR.
- Bind input through OpenXR action maps (Enhanced Input supported); use `UOpenXRInputFunctionLibrary` nodes for controller/hand state.
- For AR, use OpenXR runtime with `OpenXRAR` enabled to pin components and consume AR-tracked geometry.
- Blueprint-accessible nodes are provided for runtime checks; editor module offers project settings but no custom assets.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview reflects the OpenXR implementation present in the UE 5.7 source tree.
