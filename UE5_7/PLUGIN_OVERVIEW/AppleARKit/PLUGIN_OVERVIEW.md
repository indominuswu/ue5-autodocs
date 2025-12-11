# Apple ARKit Plugin Overview

## 1. What this plugin does
- Adds runtime support for Apple’s ARKit augmented reality system on iOS.
- Handles AR session availability, conversion of ARKit data to Unreal AR types, mesh data, textures, and face support hooks.
- Provides optional LiveLink pose tracking integration.

## 2. Key Modules
- **AppleARKit** (Runtime, PostConfigInit)
  - Role: Core ARKit session handling, frame conversion, mesh/texture support, and general AR integration.
- **AppleARKitPoseTrackingLiveLink** (Runtime, PostConfigInit)
  - Role: Modular feature that publishes ARKit body tracking data to LiveLink.

## 3. Important Types & APIs
- `FAppleARKitAvailability`
  - Role: Helper for checking device/OS compatibility and feature support.
- `FAppleARKitConversion`
  - Role: Converts ARKit tracking/geometry data to Unreal’s AR types.
- `FAppleARKitMeshData` / `FAppleARKitTextures`
  - Role: Structures carrying mesh and texture data extracted from ARKit.
- `IAppleARKitPoseTrackingLiveLink`
  - Role: Modular feature interface for LiveLink publishing.
- `UAppleARKitSettings`
  - Role: Project settings for ARKit (session options, face support toggles, recording, etc.).

## 4. Typical usage patterns
- Enable the plugin for iOS projects targeting ARKit; configure `Apple ARKit` project settings for session options and face/body support.
- Use Unreal’s AR framework components (`ARSessionConfig`, `UARBlueprintLibrary`, AR tracked geometry components); ARKit serves as the underlying provider.
- Optionally enable LiveLink pose tracking to stream ARKit body data into LiveLink consumers.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
