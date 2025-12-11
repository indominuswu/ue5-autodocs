# Google ARCore Plugin Overview

## 1. What this plugin does

- Integrates Google ARCore support for AR on Android, including tracking, camera feed, planes, images, and face data.
- Provides AR session configuration/types, Blueprint-accessible utilities, and XR tracking system integration.
- Supplies rendering support for ARCore camera passthrough and YCbCr conversion.

## 2. Key Modules

- **GoogleARCoreBase** (Runtime)  
  - Role: Core ARCore device/session integration, NDK bindings, session config, and Blueprint helpers.  
  - Notable types: `FGoogleARCoreDevice`, `FGoogleARCoreXRTrackingSystem`, `FGoogleARCoreMotionController`, `FGoogleARCoreAPI`, `FGoogleARCorePermissionHandler`, `UGoogleARCoreSessionConfig`, `UGoogleARCoreFunctionLibrary`, `UGoogleARCoreTypes`, `UGoogleARCoreAugmentedImageDatabase`, `UGoogleARCoreAugmentedImage`, `UGoogleARCoreAugmentedFace`, `UGoogleARCoreCameraImage`, `UGoogleARCoreCameraIntrinsics`.

- **GoogleARCoreRendering** (Runtime)  
  - Role: Rendering utilities for camera passthrough textures and material expressions.  
  - Notable types: `FGoogleARCorePassthroughCameraRenderer`, `UMaterialExpressionGoogleARCorePassthroughCamera`, `FGoogleARCoreYCbCrConversion`, `FGoogleARCorePassthroughCameraExternalTextureGuid`.

## 3. Important Types & APIs

### `UGoogleARCoreSessionConfig`

- Role: AR session settings (plane detection, light estimation, augmented images/faces, camera focus, update rates).
- Key properties: Enabled features (plane/faces/images), camera overlay options, light estimation mode, update rate flags.

### `UGoogleARCoreFunctionLibrary`

- Role: Blueprint-accessible ARCore utilities for session management and querying tracked geometry.
- Key functions: Enable/disable passthrough camera rendering, get camera/image intrinsics, retrieve latest camera image, query tracking status.

### Tracking/support types

- `UGoogleARCoreAugmentedImage` / `UGoogleARCoreAugmentedImageDatabase`: Manage image targets and track detected images.
- `UGoogleARCoreAugmentedFace`: Access ARCore face mesh/pose data.
- `FGoogleARCoreXRTrackingSystem`: Hooks ARCore into UE’s XR system to provide tracking and camera pose data.

### Rendering helpers

- `FGoogleARCorePassthroughCameraRenderer` and `UMaterialExpressionGoogleARCorePassthroughCamera` expose the camera texture to materials; `FGoogleARCoreYCbCrConversion` handles format conversion.

## 4. Typical usage patterns

- Enable the plugin for Android builds; create a `UGoogleARCoreSessionConfig` asset and assign it to your AR session.
- In Blueprint or C++, start the AR session with the ARCore config, then use `UGoogleARCoreFunctionLibrary` to query tracking data (planes, images, faces) and camera information.
- Use material expressions and renderer helpers to display the ARCore camera feed; leverage augmented image/face support where required.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
