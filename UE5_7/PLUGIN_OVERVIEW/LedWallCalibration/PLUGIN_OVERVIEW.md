# Led Wall Calibration Plugin Overview

## 1. What this plugin does
- Generates Aruco marker textures for LED walls and populates calibration points based on detected panels.
- Provides runtime helpers to locate parent components and build marker sets from mesh topology.
- Editor detail panel action adds calibration subpoints and Aruco textures for selected `UCalibrationPointComponent` actors.

## 2. Key Modules
- **LedWallCalibration** (Runtime)  
  - Role: Utility code to analyze calibration meshes and create Aruco marker layouts.
  - Notable types: `FLedWallCalibration`, `FLedWallArucoGenerationOptions`.
- **LedWallCalibrationEditor** (Editor)  
  - Role: Details customization for calibration points to trigger Aruco generation.
  - Notable types: `FCalibrationPointArucosForWallDetailsRow`.

## 3. Important Types & APIs

### `FLedWallCalibration`
- Role: Static helper that inspects a calibration point’s parent mesh, detects LED panels, and generates an OpenCV `cv::Mat` of Aruco markers while naming subpoints.
- Key functions: `GenerateArucosForCalibrationPoint` (builds markers and populates calibration data), `GetTypedParentComponent` (finds parent components of a given type).

### `FLedWallArucoGenerationOptions`
- Role: Blueprint-exposed struct configuring marker generation.
- Key properties: `TextureWidth`/`TextureHeight`, `ArucoDictionary`, `MarkerId` starting value, `PlaceModulus` to skip marker IDs for spacing.
- Helper: `ArucoDictionaryAsString` resolves the selected dictionary name.

### `FCalibrationPointArucosForWallDetailsRow`
- Role: Editor-only details row that drives Aruco creation for selected calibration points.
- Behavior: Remembers last dictionary and next marker ID to ease repeated runs.

## 4. Typical usage patterns
- Editor: Select calibration point actors and use the details panel action (added by the editor module) to generate Aruco markers; configure texture size/dictionary via `FLedWallArucoGenerationOptions`.
- Runtime: Use `FLedWallCalibration::GenerateArucosForCalibrationPoint` if programmatically creating marker textures and calibration subpoints from mesh data.
- Integration: Outputs textures and calibration points that can be fed into LED wall / nDisplay calibration workflows.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

