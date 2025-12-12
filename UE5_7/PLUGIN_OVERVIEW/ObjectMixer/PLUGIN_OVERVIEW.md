# Object Mixer Plugin Overview

## 1. What this plugin does
- Provides a spreadsheet-like editor for viewing and editing properties across many scene objects at once.
- Supports filtering by class/type and integrates with level/outliner selection to bulk-edit actors and components.
- Includes hidden/editor-only UI for creating custom filters, list views, and placement helpers.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor-facing Object Mixer window with filters/list views for bulk-editing actors/components (`ObjectMixerEditor` module, settings, selection integration).

## 3. Key Modules
- **ObjectMixerEditor** (Editor)  
  - Role: Main UI, filters, selection interfaces, and settings for the Object Mixer window.  
  - Notable types: `UObjectMixerEditorSettings`, `FObjectMixerEditorObjectFilter`, `FObjectMixerEditorList`/row data, `IObjectMixerSelectionInterface`, `SObjectMixerEditorList`.

## 4. Important Types & APIs
### `UObjectMixerEditorSettings`
- Role: Developer settings controlling default filter sets, UI behavior, and feature toggles for the Object Mixer.

### `FObjectMixerEditorObjectFilter`
- Role: Defines filter logic for which objects appear in the mixer (by class, tags, components, etc.).
- Key properties: filter rules for actors/components, allowed classes, include/exclude criteria.

### `IObjectMixerSelectionInterface`
- Role: Connects mixer selections with the level editor/outliner; implemented for level editor selections.

## 5. Typical usage patterns
- Enable the plugin (hidden but enabled by default) and open the Object Mixer window to view actors/components in a tabular list.
- Apply or create filters to narrow objects (by class, folder, component type) and edit exposed properties inline across multiple rows.
- Use integration with the level editor selection to sync selections between the outliner and the mixer list.

## 6. Version-specific notes (UE 5.7)
- Marked beta and hidden; no explicit UE 5.7-specific changes noted beyond the current code state.

