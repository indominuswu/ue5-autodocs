# Text 3D Plugin Overview

## 1. What this plugin does

- Creates 3D text with advanced layout, extrusion, outline, and material control.
- Provides runtime components and actors for rendering text as meshes, plus an editor workflow with style assets and font selection tools.
- Targets Virtual Production/text rendering scenarios.

## 2. Key Modules

- **Text3D** (Runtime)
  - Role: Supplies 3D text actors/components, glyph meshing, engine subsystem caching, and project settings.
- **Text3DEditor** (Editor)
  - Role: Adds asset definitions, details customizations, actor factories, and Slate panels for font and style management.

## 3. Important Types & APIs

### `UText3DComponent`

- Role: Blueprint-spawnable scene component that builds 3D text meshes from fonts and style extensions.
- Key properties/functions: `SetText`, `SetFont`, `SetFontSize`, `SetExtrude`, outline controls, uppercase enforcement, `OnTextGenerated` delegates, renderer flags.

### `UText3DActor`

- Role: Actor wrapper that hosts a `UText3DComponent` for quick placement of 3D text in a level.

### `UText3DEngineSubsystem`

- Role: Engine subsystem caching FreeType font faces and generated glyph meshes; maintains glyph mesh lookup and cleanup.

### `UText3DProjectSettings`

- Role: Project settings object for default fonts/materials and Text3D configuration.

### `UText3DStyleSet` and extension bases

- Role: Defines reusable style assets (material, geometry, layout, rendering, token extensions) that drive how text is meshed and shaded.

### Editor helpers

- `UText3DEditorFontSubsystem`, `Text3DEditor*Customization` classes, and `Text3DEditorStyleSetFactory` provide font browsing, details panels, and asset creation.

## 4. Typical usage patterns

- Enable the plugin, place a Text 3D Actor or add `UText3DComponent` to an actor, then set text, font, and extrusion/outline parameters via Details or Blueprint calls.
- Create `Text3DStyleSet` assets in the editor to bundle layout/material/rendering presets; assign them to components for consistent looks.
- Use editor font selector widgets to import or pick fonts and preview 3D text; project settings can define defaults.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
