# Media Plate Plugin Overview

## 1. What this plugin does

- Provides the `MediaPlate` actor/component for playing media textures and audio in levels.
- Supports playlists, playback control events (play/pause/open/close), and media resource management.
- Includes editor integration for placing/authoring Media Plates and attaching asset user data.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime Media Plate actor/component and Blueprint controls plus editor placement and details customization.

## 3. Key Modules

- **MediaPlate** (Runtime)
  - Role: Implements the actor/component, media resource handling, and playback control logic.
  - Notable types: `AMediaPlate`, `UMediaPlateComponent`, `FMediaPlateResource`, `UMediaPlateAssetUserData`.
- **MediaPlateEditor** (Editor)
  - Role: Editor tools and details customizations for Media Plate assets/actors.

## 4. Important Types & APIs

### `UMediaPlateComponent`

- Role: Core component that manages a media player, playlist, and playback state for a Media Plate.
- Key features: Event state enum `EMediaPlateEventState` (Play/Open/Close/Pause/Reverse/Forward/Rewind/Next/Previous), playlist management, texture/audio bindings, and resource tracking via `FMediaPlateResource`.

### `AMediaPlate`

- Role: Actor wrapper that owns a `UMediaPlateComponent` for easy placement in levels.

### `UMediaPlateAssetUserData`

- Role: Asset user data to attach Media Plate settings to mesh assets.

## 5. Typical usage patterns

- Enable the plugin and place a `MediaPlate` actor in a level; assign a media playlist/source and configure auto-play/looping as needed.
- Drive playback via the component’s events (Play/Pause/Rewind/Next/Previous) or Blueprint-accessible controls.
- Attach `UMediaPlateAssetUserData` to meshes if you need asset-level defaults for Media Plate usage.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
