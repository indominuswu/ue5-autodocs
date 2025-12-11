# Color Grading Plugin Overview

## 1. What this plugin does

- Adds an editor panel with detailed color grading controls (wheels, detail tree) for post process volumes and camera actors.
- Integrates with Object Mixer to filter/apply grading contexts.
- Includes data model generators, settings, and UI widgets for grading workflows.

## 2. Key Modules

- **ColorGradingEditor** (Editor, Default, Hidden)  
  - Role: Color grading panel, data models, UI, and integration with mixer.  
  - Notable types: `FColorGradingEditorModule`, `FColorGradingEditorDataModel`, `SColorGradingPanel`, `SColorGradingColorWheel`/`Panel`, `SColorGradingDetailView`/`Row`, `FColorGradingDetailTreeItem`, `FColorGradingDetailTreeRow`, `FColorGradingMixerObjectFilter`, `FColorGradingMixerObjectFilterRegistry`, data model generators for `CameraActor` and `PostProcessVolume`, `IColorGradingEditor`, `ColorGradingPanelState`, `ColorGradingEditorStyle`.

## 3. Important Types & APIs

- Data model: `FColorGradingEditorDataModel` aggregates grading settings; generators build models from cameras/post process volumes.  
- UI: `SColorGradingPanel` hosts wheels (`SColorGradingColorWheel`/`Panel`) and detail tree (`SColorGradingDetailView`, rows/items).  
- Mixer integration: `FColorGradingMixerObjectFilter`/`Registry` to target specific objects via Object Mixer.  
- Commands & style: `FColorGradingCommands`, `ColorGradingEditorStyle`.

## 4. Typical usage patterns

- Enable the plugin; open the Color Grading panel to adjust post process/camera color grading via wheels and detail tree.  
- Use Object Mixer filters to apply grading across selected objects; tweak panel state and settings as needed.

## 5. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted; reflects current grading UI.
