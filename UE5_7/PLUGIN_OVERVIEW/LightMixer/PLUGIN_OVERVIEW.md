# Light Mixer Plugin Overview

## 1. What this plugin does
- Provides the Light Mixer editor panel for managing scene lights in a spreadsheet-style interface.
- Integrates with Object Mixer but can hide that menu entry via settings for a lights-only workflow.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor Light Mixer panel and settings let users bulk-edit lights (optionally hiding Object Mixer entry).

## 3. Key Modules
- **LightMixer** (Editor)  
  - Role: Editor UI for bulk editing light properties.
  - Notable types: `ULightMixerEditorSettings`.

## 4. Important Types & APIs

### `ULightMixerEditorSettings`
- Role: Editor config object controlling Light Mixer visibility and menu integration.
- Key property: `bHideObjectMixerMenuItem` (removes the Object Mixer menu entry when true).

## 5. Typical usage patterns
- Editor: Open the Light Mixer panel (via Object Mixer) to tweak multiple light actors at once.
- Configure: Set `bHideObjectMixerMenuItem` if you only want the Light Mixer entry visible in menus.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin is enabled by default in the editor toolset.

