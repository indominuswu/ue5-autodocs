# Actor Palette Plugin Overview

## 1. What this plugin does
- Editor-only tool to build "actor palettes" from existing levels for quick placement.
- Lets users browse palette actors in a dedicated viewport and drag them into the level editor.
- Provides settings, commands, and styling for palette windows.

## 2. Editor/Runtime surfaces
- User-facing: Yes - editor mode with palette viewport, commands, and settings for dragging actors into levels.

## 3. Key Modules
- **ActorPalette** (Editor)
  - Role: Entirely editor-based UI/commands for creating and using actor palettes.

## 4. Important Types & APIs

### `UActorPaletteSettings`
- Role: Stores configuration for palette behavior and sourcing actors from levels.

### `FActorPaletteCommands`
- Role: Defines editor commands/shortcuts for opening palette UI and actions.

### `SActorPaletteViewport` / `FActorPaletteViewportClient`
- Role: Slate viewport showing palette actors; handles preview rendering and interaction.

## 5. Typical usage patterns
- Enable the plugin, create an Actor Palette from a level, then open the palette window to browse available actors.
- Drag actors from the palette viewport into the level editor viewport for quick placement.
- Adjust palette settings via `UActorPaletteSettings` and use toolbar/menu commands registered by the plugin.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
