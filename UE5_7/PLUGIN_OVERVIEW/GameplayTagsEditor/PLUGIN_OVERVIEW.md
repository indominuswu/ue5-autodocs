# GameplayTagsEditor Plugin Overview

## 1. What this plugin does

- Extends the editor with UI for browsing, creating, renaming, and cleaning up Gameplay Tags and tag sources.
- Adds Blueprint graph nodes for tag switches and comparisons to streamline scripting.
- Provides asset/type customizations so tags are searchable and editable in details panels and property editors.
- Supplies an asset definition and graph pin factories that render tag chips and pickers.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor tag manager UI, detail customizations, and Blueprint nodes for tag switches/compare.

## 3. Key Modules

- **GameplayTagsEditor** (UncookedOnly)  
  - Role: Editor-only tools and widgets for managing tags and exposing tag-aware Blueprint nodes.
  - Notable types: `FGameplayTagsEditorModule`, `SGameplayTagWidget`, `SGameplayTagPicker`, `SAddNewGameplayTagWidget`, `SAddNewGameplayTagSourceWidget`, `SCleanupUnusedGameplayTagsWidget`, `UGameplayTagsK2Node_SwitchGameplayTag`, `UGameplayTagsK2Node_LiteralGameplayTag`, multi-compare K2 nodes, graph pin factories, details customizations, `UAssetDefinition_GameplayTagAssetBase`.

## 4. Important Types & APIs

### `FGameplayTagsEditorModule`

- Role: Registers tag editor tabs, detail customizations, graph pin factories, and menu/toolbar entries for tag management.
- Key actions: Opens tag manager UI, handles cleanup/validation commands, wires Blueprint node factories.

### `SGameplayTagWidget` / `SGameplayTagPicker`

- Role: Slate widgets used across property editors to pick tags, show tag chips, and manage containers with filters.
- Key features: Source filtering, multi-select, search support, quick-add tags.

### Blueprint nodes (`UGameplayTagsK2Node_*`)

- Role: Provide switch/comparison logic for single tags, tag containers, and tag asset interfaces directly in Blueprint graphs.
- Key variants: Literal tag node, switch on tag/container, multi-compare against containers or asset interfaces.

### Detail/graph customizations

- Role: `FGameplayTagCustomization`, `FGameplayTagContainerCustomization`, and related search/pin factories render tag fields with proper filtering and validation in the editor.

## 5. Typical usage patterns

- Enable the plugin (automatically enabled in editor builds) and open the Gameplay Tags Manager to author project tags and tag sources.
- Use tag-aware graph pins and switch/compare nodes in Blueprints to route logic based on tags without manual string handling.
- In Details panels, pick tags via the provided widgets; customizations ensure the picker respects project tag settings and sources.
- Use cleanup UI to find unused tags and tag sources during content maintenance.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
