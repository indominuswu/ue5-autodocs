# Capture Manager Editor Plugin Overview

## 1. What this plugin does

- Provides the ingest/import side of Capture Manager for creating Unreal assets from captured archives.
- Adds editor tooling for running Live Link Hub workers, discovery, and export servers.
- Exposes developer settings to configure ingest/import behavior inside Unreal/UEFN.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor-only tooling and project settings for importing Capture Manager archives and coordinating Live Link Hub workers are configured directly by users.

## 3. Key Modules

- **CaptureManagerEditorSettings** (Editor)  
  - Role: Editor developer settings for Capture Manager import flows.
- **LiveLinkHubWorkerManager** (Editor)  
  - Role: Manages worker processes used during ingest or export.
- **LiveLinkHubExportServer** (Editor)  
  - Role: Export server for Live Link Hub interactions.
- **DataIngestCoreEditor** (Editor)  
  - Role: Editor-facing ingest utilities and UI hooks.
- **LiveLinkHubDiscoveryEditor** (Editor)  
  - Role: Discovery utilities for locating Live Link Hub services.

## 4. Important Types & APIs

- `UCaptureManagerEditorSettings` (CaptureManagerEditorSettings module)  
  - Role: Developer settings object controlling ingest/import defaults and editor integration.
- Live Link Hub worker/export/discovery managers  
  - Role: Classes in the corresponding modules handle process orchestration and discovery for Live Link Hub endpoints during ingest.

## 5. Typical usage patterns

- Enable the plugin when importing Capture Manager archives into UE/UEFN; configure `CaptureManagerEditorSettings` in project settings.
- Use Live Link Hub worker and export server modules to coordinate data transfer from capture sessions to editor assets.
- Pair with CaptureManagerCore and CaptureManagerDevices to ingest device data and generate takes/assets inside the editor.

## 6. Version-specific notes (UE 5.7)

- Editor-only plugin, disabled by default in 5.7, intended to accompany Capture Manager App/Core/Devices.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

