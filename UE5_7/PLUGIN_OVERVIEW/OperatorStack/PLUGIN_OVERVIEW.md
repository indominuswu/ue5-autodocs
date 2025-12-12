# Operator Stack Plugin Overview

## 1. What this plugin does

- Provides an editor UI for displaying and editing linked operator stacks (ordered lists of objects/settings) with a focused container-based workflow.
- Supplies custom Slate widgets, drag/drop operations, and editor customizations for stack items.
- Targets virtual production/editor scenarios where operators and parameters are organized hierarchically.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor-only operator stack panel and customization widgets.

## 3. Key Modules

- **OperatorStackEditor** (Editor)  
  - Role: Editor-only UI, styles, and customization logic for viewing and manipulating operator stacks.

## 4. Important Types & APIs

- `UOperatorStackEditorSubsystem`  
  - Editor subsystem that manages stack contexts and menu integrations.
- Slate widgets `SOperatorStackEditorPanel`, `SOperatorStackEditorStack`, `SOperatorStackEditorWidget`  
  - Main panel and stack/tree presentation for operator items.
- Builder/customization classes (`FOperatorStackEditorHeaderBuilder`, `FOperatorStackEditorBodyBuilder`, `FOperatorStackEditorStackCustomization`)  
  - Define how stack sections and items are laid out and edited.
- Item definitions (`FOperatorStackEditorItem`, `FOperatorStackEditorGroupItem`, `FOperatorStackEditorStructItem`, `FOperatorStackEditorObjectItem`)  
  - Represent different data types within a stack and handle drag/drop interactions.

## 5. Typical usage patterns

- Enable the plugin to get an editor tab/panel for operator stacks in virtual production tools.
- Use the provided subsystem to register stack contexts; items appear in the custom Slate UI with drag/drop support.
- Extend by adding new item types or customizations that derive from the provided item/customization classes.
- No runtime gameplay components; functionality is editor-only.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview reflects the Operator Stack editor utilities in the UE 5.7 source tree.
