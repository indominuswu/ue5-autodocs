# Camera Calibration Plugin Overview

## 1. What this plugin does

- Editor toolkit for lens distortion and camera calibration workflows used in Virtual Production.
- Provides calibration steps and UI for image center, nodal offset, lens distortion, and Simulcam preview.
- Adds tracking alignment runtime support and Blueprint helpers for aligning tracking systems.
- Works in conjunction with `CameraCalibrationCore` lens models and lens file assets.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Ships a calibration editor toolkit with Simulcam UI plus runtime/Blueprint tracking alignment APIs used in VP workflows.

## 3. Key Modules

- **CameraCalibrationEditor** (Editor)  
  - Role: Main calibration toolkit UI, tools, commands, and asset editors for lens files.
- **TrackingAlignment** (Runtime)  
  - Role: Runtime data structures and Blueprint library for aligning tracking data to cameras.
- **TrackingAlignmentEditor** (Editor)  
  - Role: Editor-side tools and UI for tracking alignment assets.

## 4. Important Types & APIs

- Editor toolkit & tools: `FCameraCalibrationToolkit`, `FCameraCalibrationStepsController`, `FCameraCalibrationTimeSliderController`, `FLensDistortionTool`, `FImageCenterTool`, `FNodalOffsetTool`, Slate panels `SCameraCalibrationCurveEditorPanel`, `SLensFilePanel`, `SSimulcamViewport`.
- Calibration algorithms: `FCameraCalibrationSolver`, `FCameraImageCenterAlgoManual`, `FCameraNodalOffsetAlgo*` (Aruco, Checkerboard, Manual, OpticalAxis, Points).
- Lens file handling: `ULensFileFactoryNew`, `ULensFileImporterFactory`, `FLensFileExporter`, `FLensDataCurveModel`.
- Tracking alignment runtime: `FTrackingAlignmentActors`, `UTrackingAlignmentBPLibrary`, `UTrackingAlignmentCalibrationProfile`, `FTrackingAlignmentSample`.
- Asset definitions: `UAssetDefinition_LensFile`.

## 5. Typical usage patterns

- Enable the plugin; open the Camera Calibration editor to run calibration steps (image center, lens distortion, nodal offset) using captured calibration plates.
- Create/import `LensFile` assets via the provided factories, then populate them through the calibration tools.
- For tracking alignment, create calibration profiles and use `UTrackingAlignmentBPLibrary` at runtime to align tracked cameras or apply offsets; editor tools help author samples and profiles.
- Simulcam viewport widgets (`SSimulcamViewport`) let you preview calibration results against live or recorded plates.

## 6. Version-specific notes (UE 5.7)

- Virtual Production plugin; enabled state depends on project setup.
- No explicit UE 5.7-specific notes found; overview based on current source.
