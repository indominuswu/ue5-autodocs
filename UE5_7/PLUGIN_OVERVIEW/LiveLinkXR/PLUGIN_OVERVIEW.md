# LiveLinkXR Plugin Overview

## 1. What this plugin does

- Live Link source for XR-tracked devices (motion controllers, HMDs, trackers).
- Streams transforms from the XR system into Live Link, optionally integrating with OpenXR-specific extensions.
- Supports configurable local polling rates to balance tracking smoothness and cost.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users add an XR LiveLink source (with adjustable `LocalUpdateRateInHz`) to stream HMD/controller/prop tracking into LiveLink subjects, including OpenXR integration.

## 3. Key Modules

- **LiveLinkXR** (Runtime)
  - Role: Core Live Link source for XR devices and connection settings.
  - Notable types: `ULiveLinkXRSourceSettings`, `FLiveLinkXRSource`, `ULiveLinkXRSourceFactory`.
- **LiveLinkXROpenXRExt** (Runtime)
  - Role: OpenXR extension module that hooks Live Link XR into OpenXR runtime data where available.

## 4. Important Types & APIs

### `ULiveLinkXRSourceSettings`

- Role: Live Link source settings for XR; controls the local polling rate.
- Key properties: `LocalUpdateRateInHz` (1–1000 Hz clamp).

### `FLiveLinkXRSource`

- Role: Creates/manages the XR tracking connection, reads tracked device poses, and publishes Live Link frames.
- Key behaviors: Uses connection settings to bind to device IDs and applies the configured update rate.

## 5. Typical usage patterns

- Enable the plugin, open the Live Link panel, and add an XR source; configure the polling rate as needed.
- Use the resulting Live Link subjects to drive camera rigs, tracked props, or Blueprint rigs.
- On platforms using OpenXR, the `LiveLinkXROpenXRExt` module supplies OpenXR-backed data automatically.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

