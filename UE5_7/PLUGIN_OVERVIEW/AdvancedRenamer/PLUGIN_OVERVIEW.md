# Batch Renamer Plugin Overview

## 1. What this plugin does
- Editor utility to batch-rename selected actors or assets with configurable sections (prefix/suffix, numbering, search/replace, case changes).
- Integrates into Content Browser and Level Editor for quick renaming workflows.
- Provides modular renamer sections users can combine in the UI.

## 2. Key Modules
- **AdvancedRenamer** (Editor)
  - Role: Slate UI, command bindings, and provider interfaces for renaming actors/assets.

## 3. Important Types & APIs

### Renamer sections and providers
- Section types: `UAdvancedRenamerAddPrefixSuffixSection`, `UAdvancedRenamerRemovePrefixSection`, `UAdvancedRenamerRemoveSuffixSection`, `UAdvancedRenamerSearchAndReplaceSection`, `UAdvancedRenamerNumberingSection`, `UAdvancedRenamerChangeCaseSection` implement specific rename steps.
- Providers: `FAdvancedRenamerActorProvider`, `FAdvancedRenamerAssetProvider`, `FAdvancedRenamerObjectProvider` supply rename targets.
- Base interfaces: `IAdvancedRenamerSection`, `UAdvancedRenamerSectionBase`, `IAdvancedRenamerProvider` define extensibility.

### UI and commands
- `SAdvancedRenamerPanel`, `FAdvancedRenamerCommands`, `FAdvancedRenamerStyle` deliver the editor panel and shortcuts.

## 4. Typical usage patterns
- Select actors/assets, open the Batch Renamer panel (menu/toolbar command).
- Add rename sections (prefix/suffix, numbering, search/replace, etc.) and preview results in the panel.
- Apply changes to commit the batch rename; integrations exist for Content Browser and Level Editor selections.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.