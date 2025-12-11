# Inline Material Instance Plugin Overview

## 1. What this plugin does
- Allows creating and editing material instances directly within the property editor without opening the full material editor.
- Provides dynamic parameter widgets for inline authoring of material parameters.
- Beta virtual production-focused editor feature.

## 2. Key Modules
- **InlineMaterialInstanceEditor** (Editor) - Registers the inline material instance UI and widgets.

## 3. Important Types & APIs
### `SMaterialDynamicParametersPanelWidget`
- Role: Slate panel that displays and edits dynamic material parameters inline.

### `SMaterialDynamicWidgets`
- Role: Helper widget set used by the panel to render individual parameter controls.

### `FInlineMaterialInstanceEditorModule`
- Role: Module startup responsible for hooking the widgets into the property editor flow.

## 4. Typical usage patterns
- Enable the plugin, select a material instance in the editor, and edit parameters through the inline panel embedded in Details.
- Use the dynamic widgets to tweak scalar/vector parameters without opening a separate asset editor.

## 5. Version-specific notes (UE 5.7)
- Marked Beta; no additional 5.7-only behaviors documented.
