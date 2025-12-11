# Capture Data Plugin Overview

## 1. What this plugin does

- Virtual Production plugin for managing captured data sets (images, depth, audio, metadata, calibration) used in post or alignment workflows.
- Provides runtime data assets for captured footage and meshes plus utilities for timecode parsing and validation.
- Editor module adds asset factories, definitions, and customizations for Capture Data and camera calibration records.

## 2. Key Modules

- **CaptureDataCore** (Runtime)  
  - Role: Defines Capture Data assets, metadata structures, timecode utilities, and core log/bridge helpers.
- **CaptureDataUtils** (Runtime)  
  - Role: Helper utilities for image sequences, timecode, and parsing captured takes.
- **CaptureDataEditor** (Editor)  
  - Role: Asset definitions/factories, detail customizations, and editor bridges for Capture Data and Camera Calibration assets.

## 3. Important Types & APIs

- Capture assets: `UCaptureData` (base), `UMeshCaptureData`, `UFootageCaptureData` for storing image/depth sequences, audio tracks, and references to calibration data.
- Metadata: `FCaptureMetadata`, `FCaptureTimecodeInfo`, `FCaptureTimecodeAlignment`, enums like `EFootageDeviceClass`.
- Utilities: `FImageSequenceUtils`, `FImageSequenceTimecodeUtils`, `FSoundWaveTimecodeUtils`, `FImageSequencePathChecker`, `FParseTakeUtils`.
- Editor-facing: `UAssetDefinition_CaptureData`, `UAssetDefinition_CameraCalibration`, `UCaptureDataFactory`, `UCameraCalibrationFactory`, `FCaptureMetadataCustomization`, `FCaptureDataCustomizations`, `FDeferredObjectDirtier`.
- Bridge helpers: `FCaptureDataEditorBridge`, `FCaptureDataLog`.

## 4. Typical usage patterns

- Enable the plugin to create `Capture Data` assets from recorded image/audio sequences via the provided factories.
- Populate `UCaptureData` derivatives with image sequences, depth, and audio; associate `UCameraCalibration` assets for alignment.
- Use the timecode utilities to align captured footage and audio, and the path checker to validate sequence locations.
- Editor customizations expose Capture Data properties in the Details panel; use them to configure timecode alignment and device metadata.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; overview reflects the current source.
