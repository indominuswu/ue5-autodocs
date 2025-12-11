# Variant Manager Plugin Overview

## 1. What this plugin does
- Editor toolset for creating, organizing, and activating scene actor variants (properties, functions, materials, etc.).
- Provides a custom Variant Manager panel, node views, and clipboard/drag-drop utilities for variant editing.
- Integrates with Level Variant Sets assets supplied by the VariantManagerContent plugin.
- Beta, editor-only, and disabled by default.

## 2. Key Modules
- **VariantManager** (Editor)
  - Role: Variant Manager UI, commands, property capture utilities, and editor toolkit integration.
  - Notable types: `SVariantManager`, `SVariantManagerNodeTreeView`, `LevelVariantSetsEditorToolkit`, property capture helpers (`VariantManagerPropertyCapturer`, `CapturableProperty`), blueprint helpers `VariantManagerBlueprintLibrary`.

## 3. Important Types & APIs
### `VariantManagerBlueprintLibrary`
- Role: Blueprint-accessible helpers for activating variants, switching variant sets, and querying state.

### `LevelVariantSetsEditorToolkit`
- Role: Editor toolkit for editing `LevelVariantSets` assets, hosting the Variant Manager UI.

### `SVariantManager`, `SVariantManagerNodeTreeView`, `VariantManagerDisplayNode` and subclasses
- Role: Slate UI for browsing variant sets, variants, actor bindings, and property nodes.
- Key features: drag-drop (`VariantManagerDragDropOp`), clipboard support, dependency widgets.

### `VariantManagerPropertyCapturer` / `PropertyTemplateObject`
- Role: Capture and apply property values for variants; template objects used when switching variants.

## 4. Typical usage patterns
- Enable Variant Manager (and Variant Manager Content dependency).
- Create or open a `LevelVariantSets` asset; use the Variant Manager panel to add Variant Sets and Variants.
- Capture properties or functions from actors (via the capture dialog) and arrange them in the tree.
- Use Blueprint or runtime calls (via `VariantManagerBlueprintLibrary`) to switch variants during play.

## 5. Version-specific notes (UE 5.7)
- Marked beta in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
