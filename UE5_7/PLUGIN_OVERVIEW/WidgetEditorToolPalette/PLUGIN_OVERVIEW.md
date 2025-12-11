# Tool Palette for the Widget Editor Plugin Overview

## 1. What this plugin does

- Adds a customizable tool palette to the UMG Widget Editor to speed up widget creation.
- Provides commands, styling, and default tools for spawning widgets via hotkeys and palette buttons.
- Exposes settings to define which widgets/tools appear in the palette.

## 2. Key Modules

- **WidgetEditorToolPalette** (Editor)
  - Role: Editor mode/toolkit, command bindings, default tool implementations, and settings for the palette; Windows-only.

## 3. Important Types & APIs

### `FWidgetEditorToolPaletteCommands`
- Role: Command set defining palette actions and shortcuts.

### `FWidgetEditorToolPaletteStyle`
- Role: Slate style definitions for the palette UI.

### `UWidgetEditorToolPaletteMode` / `FWidgetEditorToolPaletteToolkit`
- Role: Mode and toolkit that host the palette and tools inside the Widget Editor.

### `FCreateWidgetToolInfo` (in `CreateWidgetToolSettings`)
- Role: Config struct defining widget class, display name, hotkey, and builder class for palette entries.

### `UCreateWidgetToolSettings`
- Role: Developer settings for configuring available widget creation tools and defaults.

### Default tool builders (in `DefaultTools`)
- Role: Provide concrete widget creation behaviors referenced by the settings/builder classes.

## 4. Typical usage patterns

- Enable the plugin (editor). Configure `CreateWidgetToolSettings` to list widgets/hotkeys to appear in the palette; each entry points to a widget class and optional custom builder.
- Open the Widget Editor; the palette mode/toolkit exposes buttons and shortcuts to instantiate configured widgets directly onto the canvas.
- Extend by adding new builders under `DefaultTools` and wiring them through the settings.

## 5. Version-specific notes (UE 5.7)

- Plugin is beta and editor-only. No explicit UE 5.7-specific notes were found.
