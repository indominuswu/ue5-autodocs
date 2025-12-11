# Camera Calibration Machine Learning Plugin Overview

## 1. What this plugin does

- Reference implementation of a machine-learning-driven approach to lens distortion calibration.
- Editor-focused plugin that plugs into the Camera Calibration workflow.
- Minimal code footprint; intended as an extension point for ML-based calibrators.

## 2. Key Modules

- **CameraCalibrationML** (Editor)  
  - Role: Module stub for ML-backed calibration tooling.

## 3. Important Types & APIs

- The module currently exposes only its startup/shutdown hooks; no public classes are defined in headers.
- Extend the plugin by adding ML calibration implementations under this module if needed.

## 4. Typical usage patterns

- Enable alongside Camera Calibration when experimenting with ML-based calibration methods.
- Integrations would register additional calibration steps or algorithms within the existing Camera Calibration editor flow.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; plugin is editor-only and currently minimal.
