# Modeling Tools Editor Mode Plugin Overview

## 1. What this plugin does

- Adds the Modeling mode to the UE editor, providing interactive mesh creation and editing tools.
- Hosts the modeling tool suite UI and registers tool builders for use in the viewport.
- Offers project-level settings to customize default behaviors and tool visibility.
- Enabled for editor builds targeting modeling workflows.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor Modeling mode UI and tool registration for interactive mesh authoring.

## 3. Key Modules

- **ModelingToolsEditorMode** (Editor) — defines the Modeling editor mode, tool registration, and settings.

## 4. Important Types & APIs

- `UModelingToolsEditorMode` — editor mode entry that owns tool registration and activation.
- `UModelingToolsEditorModeSettings` — developer settings controlling Modeling mode defaults and tool enablement.
- `UModelingToolsModeCustomizationSettings` — secondary settings for customizing tool palettes and UI.
- `FEditorComponentSourceFactory` helpers — feed component sources to certain tools.

## 5. Typical usage patterns

- Enable the plugin, open the editor, and switch to Modeling mode to access mesh modeling, sculpting, and transform tools.
- Adjust `Project Settings → Plugins → Modeling Tools` to configure which tool sets are available by default.
- Extend by registering additional tool builders through the mode’s tool registration hooks.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific flags noted; content reflects the current editor mode implementation.
