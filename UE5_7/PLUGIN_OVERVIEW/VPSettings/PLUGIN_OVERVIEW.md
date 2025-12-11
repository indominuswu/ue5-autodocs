# Virtual Production Settings Plugin Overview

## 1. What this plugin does

- Stores shared virtual production configuration (camera presets, show metadata, legacy role storage) used by other VP plugins.
- Provides a single UObject (`UVPSettings`) that can be queried in-game or in-editor for defaults.
- Marked hidden/beta; primarily supporting VPRoles and Virtual Camera workflows.

## 2. Key Modules

- **VPSettings** (Runtime)  
  - Role: Defines the `UVPSettings` UObject and exposes it for Blueprint/C++ access.

## 3. Important Types & APIs

### `UVPSettings`

- Role: Config-backed UObject (config=Game) containing VP defaults.
- Key properties:
  - Virtual camera presets: `FocalLengthPresets`, `AperturePresets`, `DefaultShutterSpeedPresets`, `DefaultISOPresets`.
  - Metadata: `DirectorName`, `ShowName`.
  - Legacy roles support (`Roles`, `GetRoles()`) deprecated in favor of `UVirtualProductionRolesSubsystem`.
- Static helper: `GetVPSettings()` returns the shared settings object.

## 4. Typical usage patterns

- Enable VPSettings (automatically pulled by other VP plugins). Adjust presets and metadata in config to standardize virtual camera defaults across projects.
- Query `UVPSettings` from Blueprint or C++ to populate UI or initialize VCam components with project-standard lens/exposure presets.
- Prefer `UVirtualProductionRolesSubsystem` for machine role queries; the roles field remains only for backward compatibility.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
