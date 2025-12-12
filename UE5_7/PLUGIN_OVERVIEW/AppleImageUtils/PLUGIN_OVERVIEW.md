# Apple Image Utils Plugin Overview

## 1. What this plugin does
- Provides utilities for operating on Apple image buffers (CIImage, CVPixelBuffer, IOSurface, etc.).
- Exposes Blueprint-friendly async proxies for image conversion and resizing.
- Includes an uncooked-only module for Blueprint support helpers.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Blueprint async proxies (`UAppleImageUtilsBaseAsyncTaskBlueprintProxy`) and runtime image conversion API for Apple platforms.

## 3. Key Modules
- **AppleImageUtils** (Runtime, Default)
  - Role: Core image utility implementations and platform bridges.
- **AppleImageUtilsBlueprintSupport** (UncookedOnly, Default)
  - Role: Blueprint integration and helper classes for editor/testing.

## 4. Important Types & APIs
- `IAppleImageUtilsPlugin`
  - Role: Public interface for image conversion utilities.
- `FAppleImageUtilsImageConversionRequest` / `FAppleImageUtilsImageConversionResult`
  - Role: Types describing conversion jobs and outputs (defined in `AppleImageUtilsTypes.h`).
- `UAppleImageUtilsBaseAsyncTaskBlueprintProxy`
  - Role: Async Blueprint proxy for image conversion operations.
- `AppleImageUtilsAvailability`
  - Role: Helper for checking platform support/version constraints.

## 5. Typical usage patterns
- Enable the plugin (default on Apple platforms) and call Blueprint async nodes to convert textures/buffers to formats like PNG/JPEG/HEIF.
- Use runtime API to operate on `CIImage`/`CVPixelBuffer`/`IOSurface` sources when integrating with camera or AR feeds.
- Rely on BlueprintSupport module for editor-time testing; runtime module handles actual conversions on device.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

