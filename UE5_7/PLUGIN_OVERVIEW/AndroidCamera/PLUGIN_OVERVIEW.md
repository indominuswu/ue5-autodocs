# Android Camera Player Plugin Overview

## 1. What this plugin does
- Implements camera preview playback using the Android Camera library through the Media Framework.
- Adds runtime and editor support for configuring camera requirements and sample buffering.
- Handles Android manifest camera permissions and capability flags.
- Provides optional factory support for packaging camera media sources.

## 2. Editor/Runtime surfaces
- User-facing: Yes - provides media player factory plus project settings (`UAndroidCameraRuntimeSettings`, `UAndroidCameraSettings`) developers configure for Android camera capture.

## 3. Key Modules
- **AndroidCamera** (RuntimeNoCommandlet, PreLoadingScreen)
  - Role: Runtime media player and platform integration for Android camera capture.
- **AndroidCameraEditor** (Editor)
  - Role: Editor hooks for settings visibility and asset integration.
- **AndroidCameraFactory** (Editor, RuntimeNoCommandlet)
  - Role: Media player factory support for camera sources in editor and runtime.

## 4. Important Types & APIs
- `UAndroidCameraRuntimeSettings`
  - Role: Engine config object controlling manifest entries (permissions, required camera hardware).
  - Key properties: `bEnablePermission`, `bRequiresAnyCamera`, `bRequiresBackFacingCamera`, `bRequiresFrontFacingCamera`.
- `UAndroidCameraSettings`
  - Role: Per-project settings for media sample buffering behavior.
  - Key properties: `CacheableVideoSampleBuffers` to control whether frames are copied for reuse.

## 5. Typical usage patterns
- Enable the plugin for Android targets; configure `AndroidCamera` settings in Project Settings to set manifest requirements and permission flags.
- Adjust `CacheableVideoSampleBuffers` if external consumers need persistent frame data at the cost of performance.
- Use the provided media player factory to create camera-backed media sources for preview or in-app video feeds.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
