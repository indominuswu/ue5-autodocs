# LiveLinkOpenVR Plugin Overview

## 1. What this plugin does
- Provides a LiveLink source for OpenVR devices to stream tracking data into Unreal.
- Ships with OpenVR SDK binaries and source wrappers bundled with the plugin.

## 2. Key Modules
- **LiveLinkOpenVR** (Runtime)  
  - Role: Implements the OpenVR LiveLink source and creation UI.
  - Notable types: `ULiveLinkOpenVRSourceFactory`, `FLiveLinkOpenVRConnectionSettings`, `FLiveLinkOpenVRSource`.

## 3. Important Types & APIs

### `ULiveLinkOpenVRSourceFactory`
- Role: LiveLink source factory that builds a creation panel and constructs OpenVR sources from connection settings.
- Uses `FLiveLinkOpenVRConnectionSettings` when spawning sources.

### `FLiveLinkOpenVRSource`
- Role: LiveLink source reading tracking data from OpenVR and publishing LiveLink subjects.

## 4. Typical usage patterns
- LiveLink panel: Add a new source and select OpenVR; configure connection settings if needed.
- Runtime/editor: Consume LiveLink subjects (e.g., HMD/controllers) published by the OpenVR source to drive cameras or tracked objects.
- Note: Plugin description warns OpenVR is not supported for native arm64.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; consider the arm64 limitation noted in the plugin description.

