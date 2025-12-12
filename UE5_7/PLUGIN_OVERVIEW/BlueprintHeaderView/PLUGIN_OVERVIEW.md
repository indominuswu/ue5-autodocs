# Blueprint C++ Header Preview Plugin Overview

## 1. What this plugin does

- Displays a C++-style header preview for Blueprint classes to aid native conversion.
- Lists classes, structs, functions, and variables with generated header text in an editor widget.
- Provides settings to control the preview behavior.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor tab/widget that previews generated C++ headers for Blueprints.

## 3. Key Modules

- **BlueprintHeaderView** (Editor, Default)  
  - Role: UI and logic for rendering header previews from Blueprint metadata.  
  - Notable types: `FBlueprintHeaderViewModule`, `SBlueprintHeaderView`, `FHeaderViewClassListItem`, `FHeaderViewFunctionListItem`, `FHeaderViewStructListItem`, `FHeaderViewVariableListItem`, `UBlueprintHeaderViewSettings`.

## 4. Important Types & APIs

- `SBlueprintHeaderView`: Main Slate widget showing the generated header, plus lists for classes/structs/functions/variables.  
- List items: `FHeaderViewClassListItem`, `FHeaderViewFunctionListItem`, `FHeaderViewStructListItem`, `FHeaderViewVariableListItem` supply data to the widget.  
- Settings: `UBlueprintHeaderViewSettings` configures formatting/options.

## 5. Typical usage patterns

- Enable the plugin, open the Blueprint Header View tab for a Blueprint to inspect the equivalent C++ header layout.  
- Use to guide manual Blueprint-to-C++ migration or to understand generated class layout.

## 6. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted; reflects current preview tool behavior.
