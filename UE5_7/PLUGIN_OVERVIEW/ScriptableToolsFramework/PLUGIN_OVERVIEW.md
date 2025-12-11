# Scriptable Tools Framework Plugin Overview

## 1. What this plugin does

- Adds Blueprint-scriptable extensions to the Interactive Tools Framework (ITF) so tools and behaviors can be authored without C++.
- Provides scriptable tool base classes, behavior objects (input, hover, click/drag), and rendering/viewport helper APIs.
- Includes editor-side wrappers to register and run scriptable tools in the tooling palette.

## 2. Key Modules

- **ScriptableToolsFramework** (Runtime, PreDefault)  
  - Role: Runtime support for scriptable interactive tools, behaviors, property sets, and tool-target requirements.
- **EditorScriptableToolsFramework** (Editor)  
  - Role: Registers editor tooling for scriptable tools and exposes builder components for editor use.

## 3. Important Types & APIs

### Tool bases and behaviors

- `UScriptableInteractiveTool`, `UScriptableModularBehaviorTool`, `UScriptableSingleClickTool`, `UScriptableClickDragTool`: Scriptable ITF tool bases.
- Behavior objects such as `UScriptableToolClickDragBehavior`, `UScriptableToolKeyInputBehavior`, `UScriptableToolMouseHoverBehavior`, and `UScriptableToolViewportFocusAPI/ViewportWidgetAPI`.
- Property sets: `UScriptableInteractiveToolPropertySet`, `UEditorScriptableInteractiveToolPropertySet` for exposing editable parameters.

### Builders and helpers

- `UToolTargetScriptableToolBuilder`, `UBaseScriptableToolBuilder`, `UCustomScriptableToolBuilder`: Builders that construct scriptable tools and target requirements.
- Utility/library: `UScriptableToolsUtilityLibrary`, `UScriptableToolTargetRequirements`, geometry helpers (`UScriptableToolPointSet`, `UScriptableToolLineSet`, etc.).

### Editor integration

- `UEditorScriptableInteractiveTool` and related editor variants register scriptable tools inside the editor tool framework and wire up behaviors.

## 4. Typical usage patterns

- Enable the plugin, then create Blueprint classes deriving from the scriptable tool bases to define tool logic and behaviors.
- Define tool targets and requirements with the provided builders; assign property sets to expose adjustable parameters.
- In the editor, register the Blueprint tools via the editor module so they appear in the tool palette; use behavior objects to handle input, hover, and viewport focus.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
