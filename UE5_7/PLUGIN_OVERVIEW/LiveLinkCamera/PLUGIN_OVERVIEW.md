# LiveLinkCamera Plugin Overview

## 1. What this plugin does
- Adds LiveLink camera role support to drive cine cameras from streamed FIZ and lens data.
- Provides a camera controller component plus sequencer track/recorder to record LiveLink-driven camera changes.
- Includes editor customizations for LiveLink camera controller settings.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users attach `ULiveLinkCameraController` to cine cameras, configure lens/update flags, and record/play via the LiveLink Camera Controller Sequencer track.

## 3. Key Modules
- **LiveLinkCamera** (Runtime)  
  - Role: LiveLink camera controller logic.
  - Notable types: `ULiveLinkCameraController`.
- **LiveLinkCameraEditor** (Editor)  
  - Role: Details customization and sequencer track editor for camera controller data.
  - Notable types: `LiveLinkCameraControllerCustomization`, `LiveLinkCameraControllerTrackEditor`.
- **LiveLinkCameraRecording** (UncookedOnly)  
  - Role: Track recorder support for LiveLink camera controller data.
  - Notable types: `MovieSceneLiveLinkCameraControllerTrackRecorder`.

## 4. Important Types & APIs

### `ULiveLinkCameraController`
- Role: `ULiveLinkControllerBase` derivative that applies LiveLink camera frame data to a `UCineCameraComponent`.
- Key properties: `UpdateFlags` (per-field apply switches), `bUseCameraRange`, `LensFilePicker`, cached `LensFileEvalData`.
- Key behavior: Ticks each frame to apply FOV, aspect ratio, projection, filmback, aperture, focus distance, and mapped FIZ; validates lens tables against incoming data.

### Sequencer integration
- `MovieSceneLiveLinkCameraControllerTrack`/`Section` play back controller data in Level Sequences.
- Recorder module captures controller state during takes.

## 5. Typical usage patterns
- Runtime/editor: Attach `ULiveLinkCameraController` to a LiveLink component on a camera actor to map streamed camera data onto a cine camera. Configure update flags and optional `LensFilePicker`.
- Sequencer: Add a LiveLink Camera Controller track to record or drive camera properties when using LiveLink sources in cinematics.
- Editor UI: Use the customization panel to adjust update flags and lens mapping.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; older nodal-offset/distortion fields are marked deprecated in favor of LensComponent workflows.

