# OpenCV Lens Distortion Plugin Overview

## 1. What this plugin does
- Provides OpenCV-based camera calibration plus lens distortion/undistortion map generation.
- Supplies runtime helpers to build distortion data and apply displacement maps for compositing and camera matching.
- Includes calibration utilities to derive lens parameters from checkerboard captures.
- Depends on the OpenCV plugin for underlying math and image processing.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Exposes Blueprint/C++ APIs (`UOpenCVLensDistortionBlueprintLibrary`, `FOpenCVLensCalibrator`) that users run to calibrate cameras and generate distortion maps for compositing.

## 3. Key Modules
- **OpenCVLensCalibration** (Runtime)  
  - Role: Calibration helpers for deriving lens parameters from captured calibration images.  
  - Notable types: `FOpenCVLensCalibrator` (procedural calibrator), `IOpenCVLensCalibrationModule` interface.
- **OpenCVLensDistortion** (Runtime)  
  - Role: Blueprint-facing API to generate distortion/undistortion displacement maps and work with stored parameters.  
  - Notable types: `UOpenCVLensDistortionBlueprintLibrary`, `FOpenCVLensDistortionParameters`, `IOpenCVLensDistortionModule`.

## 4. Important Types & APIs
### `UOpenCVLensDistortionBlueprintLibrary`
- Role: Blueprint function library to generate and apply OpenCV lens distortion data.
- Key functions: build displacement maps from `FOpenCVLensDistortionParameters`, compute undistortion and overscan factors, generate cropped UV tables for rendering.

### `FOpenCVLensCalibrator`
- Role: Calibration helper that ingests calibration images to solve camera intrinsics/distortion coefficients.
- Key functions: add calibration images, solve calibration, export parameters and displacement maps for use at runtime.

### `FOpenCVLensDistortionParameters`
- Role: Struct storing camera matrix, distortion coefficients, and image size used by the Blueprint library when generating maps.

## 5. Typical usage patterns
- Capture checkerboard calibration frames, feed them to `FOpenCVLensCalibrator` (C++) or relevant Blueprint utilities, and extract `FOpenCVLensDistortionParameters`.
- Use `UOpenCVLensDistortionBlueprintLibrary` to generate distortion or undistortion displacement maps and apply them to rendered plates or camera feeds.
- Combine with compositing pipelines to align CG renders to live-action plates using calibrated camera intrinsics.

## 6. Version-specific notes (UE 5.7)
- Plugin is marked beta; no UE 5.7-specific behaviors are called out in code comments or descriptors.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

