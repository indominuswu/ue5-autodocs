# Lens Component Plugin Overview

## 1. What this plugin does
- Adds a `ULensComponent` to apply lens distortion, nodal offset, and filmback overrides to cine cameras using calibrated `ULensFile` data.
- Drives camera properties from LiveLink FIZ input, recorded values, camera settings, or manual inputs.
- Provides sequencer/editor tooling to record and edit lens component data on tracks.

## 2. Key Modules
- **LensComponent** (Runtime)  
  - Role: Actor component and runtime logic for evaluating lens files, applying distortion and nodal offsets, and syncing with LiveLink.
  - Notable types: `ULensComponent`, enums `EFIZEvaluationMode`, `EFilmbackOverrideSource`, `EDistortionSource`.
- **LensComponentEditor** (Editor)  
  - Role: Details customization and sequencer integration (tracks/recorders) for lens component properties.
  - Notable types: `MovieSceneLensComponentTrack`, `MovieSceneLensComponentSection`, `MovieSceneLensComponentTrackRecorder`, `FLensComponentDetailCustomization`.

## 3. Important Types & APIs

### `ULensComponent`
- Role: Blueprint-spawnable actor component that evaluates a `ULensFile` to drive distortion, overscan, filmback overrides, and nodal offsets on a `UCineCameraComponent`.
- Key properties: `LensFilePicker`, `EvaluationMode` (`UseLiveLink`, `UseCameraSettings`, `UseRecordedValues`, `Manual`, `DoNotEvaluate`), `DistortionStateSource`, `bApplyDistortion`, `FilmbackOverride`, `CroppedFilmback`, `bApplyNodalOffsetOnTick`.
- Key functions: `SetLensFile`, `SetFIZEvaluationMode`, `SetApplyDistortion`, `ApplyNodalOffset`, `Get/SetDistortionState`, `SetFilmbackOverrideSetting`, `SetLensFileEvaluationInputs`.
- Hooks: Reacts to LiveLink component updates to map incoming FIZ to lens evaluation; tracks original camera focal length and applies overscan when distortion is enabled.

### Sequencer support
- `MovieSceneLensComponentTrack`/`Section` allow recording and playing back lens component state in Level Sequences.
- `MovieSceneLensComponentTrackRecorder` captures lens component data during takes.

## 4. Typical usage patterns
- Editor/runtime: Attach `ULensComponent` to an actor with a `UCineCameraComponent`, assign a `ULensFile`, choose `EvaluationMode`, and enable distortion/nodal offset. Use LiveLink to stream FIZ or switch to manual/recorded inputs.
- Sequencer: Add a Lens Component track to record or keyframe lens parameters (distortion, overscan, evaluation inputs) in a Level Sequence.
- Filmback/overscan: Enable filmback override or overscan scaling to match calibrated lens data; configure via details panel added by the editor module.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; deprecated fields for nodal offset/distortion handling are kept for backward compatibility but are superseded by current `ULensComponent` behavior.

