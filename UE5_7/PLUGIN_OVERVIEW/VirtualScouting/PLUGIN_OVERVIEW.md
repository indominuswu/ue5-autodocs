# Virtual Scouting Plugin Overview

## 1. What this plugin does

- Provides a VR-focused scouting experience for filmmakers to explore digital environments.
- Integrates OpenXR, Enhanced Input, CommonUI, Multi-User, LiveLink, and VP utilities to deliver in-headset tools.
- Ships with per-project and per-user settings to tailor movement, viewfinder exposure, and tool collections.

## 2. Key Modules

- **VirtualScoutingOpenXR** (Runtime) – OpenXR integration and platform-specific hooks for the scouting toolset.
- **VirtualScouting** (Runtime) – Core runtime behaviors and settings that drive the VR scouting experience.
- **VirtualScoutingEditor** (Editor) – Editor integrations for launching/configuring the scouting session and tooling.

## 3. Important Types & APIs

### `UVirtualScoutingSettings`

- Role: Project-level developer settings for the scouting experience.
- Key properties: `bUseImperial`, `bViewfinderUseExposure`, `ViewfinderExposureCompensation`, aperture/mask presets, `SequenceToolCollection`, `PlacementToolCollection`, `bSwapToGrabToolOnSpawnNewActor`.
- Static helper: `GetVirtualScoutingSettings()` to retrieve the settings object.

### `UVirtualScoutingEditorSettings`

- Role: User/editor preferences for VR comfort and UI feedback.
- Key properties: `FlightSpeed`, `DragSpeed`, `bEnableTooltips`, `bUseSmoothRotation`, `bUseTeleportRotation`.
- Static helper: `GetVirtualScoutingEditorSettings()`.

## 4. Typical usage patterns

- Enable Virtual Scouting and required dependencies (OpenXR, EnhancedInput, VirtualProductionUtilities, etc.).
- Configure project defaults in Project Settings → Virtual Scouting (units, exposure, tool collections).
- Set per-user comfort preferences (flight/drag speed, rotation style, tooltips) in Editor Per-Project User Settings.
- Launch a Virtual Scouting session (via editor tooling) to explore the level in VR; tool collections determine available placement/sequence tools in-headset.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
