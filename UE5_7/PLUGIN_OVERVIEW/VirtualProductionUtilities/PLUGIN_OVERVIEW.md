# Virtual Production Utilities Plugin Overview

## 1. What this plugin does

- Provides a grab-bag of runtime and editor utilities for virtual production (bookmarks, timecode, UI wrappers, root actors).
- Includes Blueprint libraries and helper actors for setting up VP-friendly worlds, overlays, and rendering tweaks.
- Supplies bookmark types/editor support for saving and restoring VP views and states.

## 2. Key Modules

- **VPUtilities** (Runtime) – Core runtime utilities, actors, and Blueprint libraries for VP scenes.
- **VPUtilitiesEditor** (Editor) – Editor customizations, VR tools, scouting subsystem, and settings for VP utilities.
- **VPBookmark** (UncookedOnly) – Bookmark asset/runtime implementation for VP bookmarks.
- **VPBookmarkEditor** (Editor) – Editor UI and Blueprint helpers for working with VP bookmarks.

## 3. Important Types & APIs

### Runtime actors & components

- `AVPRootActor`: Root actor for grouping VP systems; sets up common components and categories.
- `AVPBookmarkActor`: Bookmark actor with stored camera/location info; pairs with `UVPBookmark` asset and `UVPBookmarkSettings`.
- `AVPFullScreenUserWidgetActor`: Places a user widget fullscreen in-game or in-editor.
- `AVPPassthroughPostProcessVolume`: Post-process volume tuned for VP passthrough.
- `UVPTimecodeCustomTimeStep`: Custom time step sourcing from timecode.

### Blueprint libraries

- `UVPBlueprintLibrary`, `UVPCameraBlueprintLibrary`, `UVPRenderingBlueprintLibrary`: Helpers for common VP actions (camera/viewport setup, rendering toggles).
- `UVPBookmarkBlueprintLibrary` and editor counterpart `UVPBookmarkEditorBlueprintLibrary`: Create, save, and restore VP bookmarks.

### Editor subsystems & settings

- `UVPScoutingSubsystem` variants (editor-only): Base/derived classes for VR scouting utilities.
- `UVPUtilitiesEditorSettings` & `UVPBookmarkSettings`: Configurable defaults for VP utilities/bookmarks; includes editor-per-project user settings.
- Tickable editor actor bases (`UVPEditorTickableActorBase`, `UVPTransientEditorTickableActorBase`, `UVPViewportTickableActorBase`) for tools that need editor ticks.

## 4. Typical usage patterns

- Enable the plugin (and dependencies like VPRoles/VPSettings). Place `VPRootActor` to anchor VP helpers in a level.
- Use `VPBookmark` assets/actors to capture and restore camera/view states; drive them via Blueprint libraries or the bookmark editor UI.
- Add `VPFullScreenUserWidgetActor` to display UI overlays, or use `UVPTimecodeCustomTimeStep` for timecode-driven playback.
- In the editor, configure settings under Virtual Production Utilities and leverage `UVPScoutingSubsystem` implementations for VR scouting tools.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
