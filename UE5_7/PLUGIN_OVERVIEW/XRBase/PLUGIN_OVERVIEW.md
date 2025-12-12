# XRBase Plugin Overview

## 1. What this plugin does
- Supplies foundational XR rendering, tracking, and Blueprint utilities used by XR runtimes.
- Implements default cameras, loading screens, stereo layer helpers, copy-texture utilities, and tracking system base classes.
- Exposes Blueprint libraries for XR device queries, motion tracking, hand tracking, and device visualization.
- Includes editor support for XR device visualization property panels; typically auto-enabled by dependent XR plugins.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Provides runtime Blueprint libraries/components for XR devices and editor detail customizations for device visualization.

## 3. Key Modules
- **XRBase** (Runtime): Core XR utilities, rendering bridges, tracking system bases, Blueprint libraries, and components.
- **XRBaseEditor** (Editor): Custom detail panels and tooling for XR device visualization and related editor hooks.

## 4. Important Types & APIs
- `FXRTrackingSystemBase`: Base implementation of `IXRTrackingSystem`; handles device enumeration, tracking origin changes, loading screens, motion/hand tracking queries, and delegates (`OnXRTrackingOriginChanged`, `OnXRPlayAreaChanged`, `OnXRInteractionProfileChanged`).
- `FDefaultXRCamera` (`IXRCamera`, `FHMDSceneViewExtension`): Default camera for XR devices with view extension support.
- `FDefaultXRLoadingScreen` / `TXRLoadingScreenBase`: Loading screen management with stereo layer rendering helpers.
- `FXRRenderBridge`, `FXRRenderTargetManager`, `FXRSwapChain`, `AddXRCopyTexturePass`: Rendering primitives for XR backends and compositing.
- Blueprint libraries:
  - `UHeadMountedDisplayFunctionLibrary`: Cross-XR device queries, poses, hand/motion controller data, timed input delegates, remote XR device connection helpers.
  - `UMotionTrackedDeviceFunctionLibrary`: Motion tracking enable/disable and device identification helpers.
  - `UXRAssetFunctionLibrary`: Spawn static-mesh visualization components for XR devices (blocking/async, by name or device id).
  - `UXRLoadingScreenFunctionLibrary`: Manage XR loading screen images, splashes, and show/hide behavior.
- Components: `UXRDeviceVisualizationComponent` (renders XR device meshes), `UVRNotificationsComponent` (broadcasts VR lifecycle events).

## 5. Typical usage patterns
- XR runtime plugins derive their tracking systems from `FXRTrackingSystemBase` and reuse default camera/loading screen utilities.
- Game teams use Blueprint libraries to query devices, get poses, and spawn visualization components for controllers/HMDs.
- Add `UVRNotificationsComponent` to actors to receive connection, HMD recenter, and similar events.
- Editor tooling (XRBaseEditor) customizes device visualization details panes for XR assets.

## 6. Version-specific notes (UE 5.7)
- Shipping as a core dependency with optional LiveLinkHub support; no UE 5.7-specific deltas explicitly noted.
