# StateTree Plugin Overview

## 1. What this plugin does
- Provides a general-purpose hierarchical state machine system for gameplay.
- Supports Blueprint-authorable tasks, evaluators, conditions, and considerations.
- Includes editor tooling and developer/test modules for authoring and validating state trees.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Includes a StateTree asset editor, Blueprint node bases, and runtime helpers used directly in gameplay scripting.

## 3. Key Modules
- **StateTreeModule** (Runtime)
  - Role: Core runtime for evaluating state trees and hosting Blueprint node bases.
  - Notable types: `UStateTreeNodeBlueprintBase`, `UStateTreeTaskBlueprintBase`, `UStateTreeEvaluatorBlueprintBase`, `UStateTreeConditionBlueprintBase`, `UStateTreeFunctionLibrary`, `UStateTreeSettings`.
- **StateTreeDeveloper** (DeveloperTool)
  - Role: Developer-oriented utilities for profiling or debugging state trees.
- **StateTreeEditorModule** (UncookedOnly)
  - Role: Editor integration, UI layers, and settings for the StateTree asset editor.
  - Notable types: `UStateTreeEditingSubsystem`, `UStateTreeEditorSettings`, `UStateTreeEditorUserSettings`, `UStateTreeEditorUISubsystem`, `UK2Node_StateTreeBlueprintPropertyRef`.
- **StateTreeTestSuite** (UncookedOnly)
  - Role: Automated test coverage for StateTree features.

## 4. Important Types & APIs
- `UStateTreeNodeBlueprintBase` (base for tasks/evaluators/conditions)
  - Role: Base class used by Blueprintable nodes; provides access to execution context.
- `UStateTreeTaskBlueprintBase`, `UStateTreeEvaluatorBlueprintBase`, `UStateTreeConditionBlueprintBase`
  - Role: Specialized node bases for authoring task logic, evaluators, and conditions.
- `UStateTreeFunctionLibrary`
  - Role: Blueprint helper library for interacting with state trees at runtime.
- `UStateTreeSettings` (UDeveloperSettings)
  - Role: Project-level StateTree configuration.
- `UStateTreeEditingSubsystem` (UEditorSubsystem)
  - Role: Editor service managing StateTree asset editing lifecycle and UI integration.
- `UStateTreeEditorSettings` / `UStateTreeEditorUserSettings`
  - Role: Editor and per-user settings controlling editor behavior and defaults.

## 5. Typical usage patterns
- Enable the plugin and its dependencies (GameplayInsights for editor profiling; PropertyAccessEditor/PropertyBindingUtils for bindings).
- Create StateTree assets and author tasks/evaluators/conditions via the editor module; use the editor subsystem/UI layers provided.
- At runtime, run StateTree instances through the StateTreeModule API, invoking Blueprint nodes derived from the provided base classes.
- Use developer and test modules in uncooked builds for validation and debugging.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
