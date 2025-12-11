# MetaHuman Animator Calibration Diagnostics Plugin Overview

## 1. What this plugin does
- Experimental diagnostics tools for MetaHuman Animator calibration sessions.
- Provides UI to inspect calibration imagery, compute errors, and visualize feature matching results.
- Supplements the main MetaHuman calibration workflow with reporting/QA utilities.

## 2. Key Modules
- **MetaHumanCalibrationDiagnostics** (Editor)
  - Role: Hosts the diagnostics window, image viewer widgets, commands, and error calculators.
  - Notable types: `SCalibrationDiagnosticsWindow`, `SCalibrationDiagnosticsImageViewer`, `FMetaHumanCalibrationDiagnosticsCommands`, `FMetaHumanCalibrationErrorCalculator`, `UMetaHumanRobustFeatureMatcher`, `FMetaHumanCalibrationDiagnosticsOptions`.

## 3. Important Types & APIs
### `FMetaHumanCalibrationErrorCalculator`
- Role: Computes error metrics across calibration frames to highlight problematic camera data.

### `UMetaHumanRobustFeatureMatcher`
- Role: Performs feature matching on calibration imagery to support diagnostics and visualization.

### `SCalibrationDiagnosticsWindow` / `SCalibrationDiagnosticsImageViewer`
- Role: Editor widgets that display calibration frames, overlays, and error results in a dedicated diagnostics window.

## 4. Typical usage patterns
- Enable the plugin (Experimental/MetaHuman). Open the Calibration Diagnostics window from the MetaHuman calibration tools.
- Load calibration captures; use the image viewer to inspect feature matches and review error metrics.
- Adjust capture setup based on reported errors before running final calibration/solve.

## 5. Version-specific notes (UE 5.7)
- Marked experimental; no additional UE 5.7-specific notes found in the source.
