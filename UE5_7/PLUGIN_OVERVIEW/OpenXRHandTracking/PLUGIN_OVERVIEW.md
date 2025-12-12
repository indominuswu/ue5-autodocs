# OpenXR Hand Tracking Plugin Overview

## 1. What this plugin does

- Implements the `XR_EXT_hand_tracking` OpenXR extension for skeletal hand tracking.
- Publishes hand joints through LiveLink and optional remapping assets for animation/retargeting.
- Provides editor settings for enabling hand tracking and LiveLink source configuration.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Exposes OpenXR hand joints via LiveLink (`ULiveLinkOpenXRHandTrackingSourceFactory`/remap assets) and project settings so developers can drive animation Blueprints for XR hands.

## 3. Key Modules

- **OpenXRHandTracking** (Runtime)  
  - Role: Registers hand-tracking support with OpenXR and feeds joint transforms to LiveLink/engine systems.
- **OpenXRHandTrackingEditor** (Editor)  
  - Role: Editor configuration and assets (remap asset type, settings UI).

## 4. Important Types & APIs

- `IOpenXRHandTrackingModule`  
  - Module interface to access hand-tracking availability and setup.
- `FOpenXRHandTracking` (`OpenXRHandTracking.h`)  
  - Core runtime that queries joint poses from OpenXR and pushes them into LiveLink subjects.
- `UOpenXRHandTrackingSettings`  
  - Settings object for enabling features (e.g., aim/aim pose, mesh support).
- `ULiveLinkOpenXRHandTrackingSourceFactory`, `UOpenXRHandTrackingLiveLinkRemapAsset`  
  - LiveLink source factory and remapping asset for converting OpenXR joint data to desired skeleton hierarchies.

## 5. Typical usage patterns

- Enable together with the core OpenXR plugin and enable the hand-tracking extension in Project Settings.
- In LiveLink, add the OpenXR hand-tracking source to stream joint transforms; use remap assets to fit custom skeletons.
- Consume joint data in animation Blueprints (e.g., driving hand poses for XR avatars); no runtime Blueprint nodes are added beyond standard LiveLink use.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview reflects the hand-tracking extension support in the UE 5.7 source tree.

