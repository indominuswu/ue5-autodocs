# Capture Manager Devices Plugin Overview

## 1. What this plugin does

- Adds device implementations usable from the Capture Manager layout inside Live Link Hub.
- Provides ingest devices for mono and stereo video, CPS/Live Link face capture, and archive/take ingest.
- Supplies common video Live Link device utilities shared across the ingest devices.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Live Link Hub users add and configure these ingest devices in the Capture Manager UI; exposes per-device settings objects for user configuration.

## 3. Key Modules

- **MonoVideoIngestDevice** (Editor)  
  - Role: Mono video ingest device for Capture Manager.
- **CPSLiveLinkDevice** (Editor)  
  - Role: CPS/Live Link face device integration.
- **TakeArchiveIngestDevice** (Editor)  
  - Role: Ingests archived take data.
- **StereoVideoIngestDevice** (Editor)  
  - Role: Stereo video ingest device handling stereo-specific settings.
- **VideoLiveLinkDeviceCommon** (Editor)  
  - Role: Shared utilities and base device helpers for video Live Link ingest.

## 4. Important Types & APIs

- `ULiveLinkFaceDeviceSettings` / `ULiveLinkFaceDevice` (CPSLiveLinkDevice)  
  - Role: Settings and implementation for the CPS/Live Link face device.
- `UMonoVideoIngestDeviceSettings` / `UStereoVideoIngestDeviceSettings`  
  - Role: Device settings objects defining ingest configuration.
- `UTakeArchiveIngestDeviceSettings`  
  - Role: Settings for archive/take ingest device.
- `ULiveLinkDeviceSettings` (shared)  
  - Role: Base Live Link device settings used across ingest device implementations.

## 5. Typical usage patterns

- Enable alongside Capture Manager App and use the Live Link Hub Capture Manager layout to add ingest devices from this plugin.
- Configure per-device settings (mono/stereo/face/archive) in the Capture Manager UI to match incoming capture sources.
- Use devices in ingest jobs to stream or import media into Unreal for later conversion and asset creation.

## 6. Version-specific notes (UE 5.7)

- All modules are Editor-only and disabled by default in this UE 5.7 build.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

