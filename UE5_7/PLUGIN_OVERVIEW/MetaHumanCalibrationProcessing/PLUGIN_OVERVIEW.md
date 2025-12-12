# MetaHuman Animator Calibration Processing Plugin Overview

## 1. What this plugin does
- Provides the calibration processing pipeline for MetaHuman Animator, including feature matching, stereo calibration, and rig utilities.
- Ships with a large native calibration library (camera models, bundle adjustment, robust feature matching, rig logic helpers).
- Adds editor widgets and generators to drive calibration workflows and visualize frames.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor calibration workflows with UI/widgets for MetaHuman Animator processing.

## 3. Key Modules
- **MetaHumanCalibrationLib** (Editor)
  - Role: Core calibration library (C++ and third-party code) for camera models, robust feature matching, bundle adjustment, and rig utilities.
  - Notable types: `FMetaHumanStereoCalibrator`, `FMetaHumanRobustFeatureMatcher`, `FMetaHumanCalibrationLib`, camera/rig/math utilities under `calib`, `robustfeaturematcher`, `rig`, and `nls` namespaces.
- **MetaHumanCalibrationCore** (Editor)
  - Role: Shared UI/utility layer for calibration; widgets like `SMetaHumanSingleImageViewer`, `SMetaHumanCalibrationObjectWidget`, and helpers (`FMetaHumanCalibrationUtils`, `FMetaHumanCalibrationFrameResolver`, `FMetaHumanCalibrationNotificationManager`).
- **MetaHumanCalibrationGenerator** (Editor)
  - Role: Generator workflow and windows for running calibration sequences.
  - Notable types: `FMetaHumanCalibrationGenerator`, `SMetaHumanCalibrationGeneratorWindow`, `SMetaHumanCalibrationImageViewer`, `FMetaHumanCalibrationAutoFrameSelector`.

## 4. Important Types & APIs
### `FMetaHumanStereoCalibrator`
- Role: Performs stereo camera calibration and parameter estimation for MetaHuman capture setups.

### `FMetaHumanRobustFeatureMatcher`
- Role: Matches features across images for calibration; used by diagnostics/generator flows.

### `FMetaHumanCalibrationGenerator` / `FMetaHumanCalibrationGeneratorState`
- Role: Drives calibration runs, managing options, progress, and output data.
- Key settings: generator options (`FMetaHumanCalibrationGeneratorOptions`), auto frame selection, pattern detection, and area-of-interest helpers.

### Calibration core widgets/utilities
- `SMetaHumanSingleImageViewer`, `SMetaHumanImageViewerScrubber`, `SMetaHumanCalibrationObjectWidget` support previewing calibration images and overlaying results.
- Utility classes under `MetaHumanCalibrationUtils` and `MetaHumanCalibrationNotificationManager` provide helper math and user messaging.

## 5. Typical usage patterns
- Enable the plugin (MetaHuman). Use the Calibration Generator window to run stereo calibration on captured frames.
- Configure generator options (frame selection, pattern detection), run the process, and inspect results via the provided viewers.
- Use the core library in custom tools to perform feature matching or camera calibration programmatically.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; the plugin ships with extensive third-party calibration code in this release.
