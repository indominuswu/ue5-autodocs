# Scriptable Tools Editor Mode Plugin Overview

## 1. What this plugin does
- Adds an editor mode dedicated to Scriptable Tools (built on ScriptableToolsFramework).
- Provides UI and settings to organize scriptable tool groups and tags, integrating with modeling tools.
- Includes custom details/UI widgets for selecting tool groups and tags inside the editor.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor mode, toolkit, and widgets for managing scriptable tool groups/tags.

## 3. Key Modules
- **ScriptableToolsEditorMode** (Editor)  
  - Role: Registers the editor mode, toolkit, commands, settings, and UI widgets for managing scriptable tool groups.  
  - Notable types: `FSimpleScriptableToolsEditorMode` (mode), `UScriptableToolsModeCustomizationSettings`, `FScriptableToolsEditorModeToolkit`, UI widgets (`SScriptableToolGroupSetPicker`, `SScriptableToolGroupSetCombo`), and customizations for group/tag selection.

## 4. Important Types & APIs
### `UScriptableToolsModeCustomizationSettings`
- Role: Developer settings for scriptable tool groups/tags used by the mode UI.
- Key properties: default group sets, visibility toggles, tag customization options.

### `FSimpleScriptableToolsEditorMode` (defined in `ScriptableToolsEditorMode.h`)
- Role: Editor mode that exposes scriptable tools and initializes the toolkit/commands.
- Key behaviors: registers scriptable tool groups, binds commands, manages activation lifecycle.

### UI widgets (`SScriptableToolGroupSetPicker`, `SScriptableToolGroupSetCombo`)
- Role: Allow users to pick which scriptable tool group set/tag set is active inside the mode.

## 5. Typical usage patterns
- Enable the plugin (beta) and enter the Scriptable Tools editor mode to run script-driven tools authored with ScriptableToolsFramework.
- Configure group/tag defaults in `UScriptableToolsModeCustomizationSettings`, then use the picker widgets to switch groups at runtime.
- Combine with MeshModelingToolset to mix scriptable tools with modeling workflows.

## 6. Version-specific notes (UE 5.7)
- Marked beta and disabled by default; no explicit UE 5.7-specific notes in code comments.
