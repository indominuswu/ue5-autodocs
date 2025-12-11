# Stage Monitor Plugin Overview

## 1. What this plugin does
- Supports monitoring workflows for virtual production stages with multiple machines.
- Provides shared interfaces for stage monitor sessions, data providers, and common utilities.
- Includes editor configuration and tooling for the monitor UI and data export.

## 2. Key Modules
- **StageMonitor** (UncookedOnly)
  - Role: Core monitor interfaces for sessions and session management.
  - Notable types: `IStageMonitor`, `IStageMonitorSession`, `IStageMonitorSessionManager`, `IStageMonitorModule`.
- **StageMonitorEditor** (Editor)
  - Role: Editor-side settings and utilities for the stage monitor experience.
  - Notable types: `UStageMonitorEditorSettings`.
- **StageDataProvider** (Runtime)
  - Role: Data provider module exposing the monitor data feed; entry point `IStageDataProviderModule`.
- **StageMonitorCommon** (Runtime)
  - Role: Shared settings and helpers used by monitor clients/providers.
  - Notable types: `UStageMonitoringSettings`, `FStageDataExportSettings`, `FStageFramePerformanceSettings`, `FStageHitchDetectionSettings` (and other settings structs).

## 3. Important Types & APIs
- `IStageMonitor`, `IStageMonitorSession`, `IStageMonitorSessionManager`
  - Role: Abstract interfaces defining how monitors discover, open, and manage monitoring sessions.
- `UStageMonitoringSettings` (UDeveloperSettings)
  - Role: Configurable settings for message filtering, export, and performance thresholds.
- `UStageMonitorEditorSettings`
  - Role: Editor-only settings controlling monitor UI behavior.
- `IStageDataProviderModule`
  - Role: Module interface for providers publishing stage data to monitors.

## 4. Typical usage patterns
- Enable the plugin (Beta) together with Virtual Production utilities; configure `UStageMonitoringSettings` for message filters/export preferences.
- Implement or use an `IStageDataProviderModule` to publish stage data; connect monitors via `IStageMonitorSessionManager`.
- In the editor, adjust `UStageMonitorEditorSettings` and use the monitor UI/tools to observe connected machines, hitch detection, or performance metrics.
- Export session data using the settings-driven filters provided by StageMonitorCommon.

## 5. Version-specific notes (UE 5.7)
- Marked Beta in the `.uplugin`; no additional UE 5.7-specific notes found.
