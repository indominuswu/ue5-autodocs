# MetaHuman Creator Plugin Overview

## 1. What this plugin does
- MetaHuman character asset creator and editor for assembling MetaHuman components (skin, eyes, teeth, makeup, materials).
- Provides runtime asset definitions plus editor palettes, migration helpers, and default pipelines for generated assets.
- Integrates with MetaHuman Creator import flows and supports palette-based component management.

## 2. Key Modules
- **MetaHumanCharacter** (Runtime)
  - Role: Core MetaHuman character data, component definitions, and runtime defaults.
  - Notable types: `UMetaHumanCharacter`, `FMetaHumanCharacterEyes`, `FMetaHumanCharacterSkin`, `FMetaHumanCharacterTeeth`, `FMetaHumanCharacterMakeup`, `FMetaHumanCharacterMaterialSet`, `FMetaHumanCharacterGeneratedAssets`.
- **MetaHumanCharacterEditor** (Editor)
  - Role: Asset editor/palette UI, migration helpers, and pipelines for authoring MetaHuman character assets.
  - Notable types: `FMetaHumanCharacterEditorModule`, editor palette/toolkit classes, `UMetaHumanCharacterMigrationEditor`.
- **MetaHumanCharacterPalette** (Runtime) / **MetaHumanCharacterPaletteEditor** (Editor)
  - Role: Palette data and editor UI for selecting component variants.
- **MetaHumanDefaultPipeline** (Runtime) / **MetaHumanDefaultEditorPipeline** (Editor)
  - Role: Default pipelines for generating and editing MetaHuman character assets.

## 3. Important Types & APIs
### `UMetaHumanCharacter`
- Role: Central MetaHuman character asset storing component selections, material sets, and generated asset references.
- Key properties: assembly settings (`FMetaHumanCharacterAssemblySettings`), skin/eye/teeth/makeup options, viewport settings (`FMetaHumanCharacterViewport`).

### Palette and pipeline helpers
- `MetaHumanCharacterPalette` assets store selectable component variants; editor palette module exposes UI to choose and apply them.
- Default pipeline modules (`MetaHumanDefaultPipeline`, `MetaHumanDefaultEditorPipeline`) orchestrate generation/import of assets from palette selections.

### Migration/editor utilities
- Editor module includes migration support (`MetaHumanCharacterMigrationEditor`) for updating existing MetaHuman assets to new formats.

## 4. Typical usage patterns
- Enable the plugin. Create or import a MetaHuman Character asset and open it in the MetaHuman character editor.
- Use the palette UI to pick components (skin, eyes, teeth, makeup) and adjust assembly settings.
- Run the default pipeline to generate/update associated assets; use migration tools when upgrading older MetaHumans.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin is disabled by default in this release.
