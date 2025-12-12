# Camera Calibration Core Plugin Overview

## 1. What this plugin does

- Core runtime and editor support for lens distortion models, lens files, and calibration utilities used by Camera Calibration tooling.
- Provides lens model handlers, data tables, and scene view extensions for distortion rendering and correction.
- Supplies a calibration subsystem and settings for project-wide camera calibration data.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Provides editor customizations and runtime lens calibration subsystem/data structures consumed by Camera Calibration tooling and calibrated rendering workflows.

## 3. Key Modules

- **CameraCalibrationCore** (Runtime)  
  - Role: Lens data structures, distortion model handlers, lens files, rendering extensions, calibration subsystem, and utilities.
- **CameraCalibrationCoreEditor** (Editor)  
  - Role: Editor customizations for calibration components and lens distortion settings.

## 4. Important Types & APIs

- Subsystem & settings: `UCameraCalibrationSubsystem`, `UCameraCalibrationSettings`.
- Lens data & files: `FLensData`, `ULensFile`, `BaseLensTable` derivatives (`FocalLengthTable`, `ImageCenterTable`, `DistortionParametersTable`, `NodalOffsetTable`, `EncodersTable`, `STMapTable`), `FLensFileRendering`.
- Distortion models & handlers: `FLensDistortionModelHandlerBase`, `FAnamorphicLensDistortionModelHandler`, `FBrownConradyDULensDistortionModelHandler`, `FBrownConradyUDLensDistortionModelHandler`, `FSphericalLensDistortionModelHandler`, plus model definitions (`FAnamorphicLensModel`, `FBrownConrady*`, `FSphericalLensModel`).
- Rendering integration: `FLensDistortionSceneViewExtension`, `FOverlayRendering`, `FDistortionRenderingUtils`.
- Calibration helpers: `UCalibrationPointComponent`, `FCameraCalibrationCheckerboard`, `FCameraCalibrationStep`, `FLensInterpolationUtils`, `FLensTableUtils`, `ICalibratedMapProcessor` and formats for calibration maps.
- Editor customizations: `FCalibrationPointComponentDetails`, `FLensDistortionStateDetailCustomization`, `FCalibrationPointComponentDetailsRow`.

## 5. Typical usage patterns

- Enable the plugin (required by Camera Calibration) to access lens data structures and distortion rendering support.
- At runtime or in editor tools, load/create `ULensFile` assets to store lens parameters; use `UCameraCalibrationSubsystem` to access lens data for distortion correction.
- Choose and configure a lens distortion model handler appropriate to the physical lens; apply via `FLensDistortionSceneViewExtension` when rendering calibrated cameras.
- Use calibration point components and table utilities in custom calibration workflows or when extending the Camera Calibration editor.

## 6. Version-specific notes (UE 5.7)

- Ships as part of UE 5.7 Virtual Production stack; no explicit version-specific flags noted.
- No explicit UE 5.7-specific notes found; overview reflects current source.
