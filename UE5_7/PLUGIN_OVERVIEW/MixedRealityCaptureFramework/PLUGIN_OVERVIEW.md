# Mixed Reality Capture Framework Plugin Overview

## 1. What this plugin does

- Provides a runtime framework for capturing mixed reality (VR + real-world camera) video.
- Supplies actor and component support for aligning tracked cameras, garbage mattes, and compositing feeds.
- Includes Blueprint helpers to drive calibration, video device selection, and utility math for MR capture.
- Disabled by default; targeted at VR projects needing composited mixed reality output.

## 2. Key Modules

- **MixedRealityCaptureFramework** (Runtime) — core MR capture components, calibration data, device plumbing, and Blueprint utilities.

## 3. Important Types & APIs

- `AMixedRealityCaptureActor` — actor shell hosting the capture component setup.
- `UMixedRealityCaptureComponent` — main component handling tracked camera pose, compositing, and MR capture.
- `UMrcGarbageMatteCaptureComponent` — captures garbage mattes to improve compositing quality.
- `UMrcFrameworkSettings` — configurable MR capture settings container.
- `UMrcUtilLibrary` — Blueprint function library for MR capture helpers (camera/component utilities).
- `UMrcVideoCaptureDevice` — describes available capture devices and selection helpers.
- Interfaces `IMrcFrameworkModule`, `IMrcFocalDriver` — extension points for framework and focal calibration.

## 4. Typical usage patterns

- Enable the plugin, add an `AMixedRealityCaptureActor` (or `UMixedRealityCaptureComponent`) to a VR level, and bind it to a physical camera or motion controller.
- Use `UMrcGarbageMatteCaptureComponent` to record garbage mattes for better foreground isolation.
- Drive calibration and device selection through `UMrcUtilLibrary` Blueprint nodes and `UMrcFrameworkSettings`.
- Align MR camera pose with motion controllers or tracked references, then composite the feed into the viewport or recording pipeline.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific behavior flagged; plugin remains optional and off by default.
