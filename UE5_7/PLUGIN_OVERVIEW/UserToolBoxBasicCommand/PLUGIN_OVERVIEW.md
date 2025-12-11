# UserToolBoxBasicCommand Plugin Overview

## 1. What this plugin does

- Supplies a library of ready-to-use editor commands and filters for the UserToolBox framework.
- Includes commands for selection isolation, layer/level assignment, view mode toggles, console variables, Python execution, mesh utilities, and composite command chaining.
- Extends the UserToolBox UI so non-programmers can assemble workflows from prebuilt actions.

## 2. Key Modules

- **UserToolBoxBasicCommand** (Editor)  
  - Role: Registers the built-in command assets and command classes used by UserToolBoxCore.  
  - Notable types: `UBaseActorFilter` subclasses, `UAssignToLayer`, `UAssignToLevel`, `UChangeViewMode`, `UExecutePythonScript`, `UConsoleVariable`, `UCompositeCommand`/`UCompositeInlineCommand`, `UToggleCommand`, `UMergeCommand`, etc.

## 3. Important Types & APIs

- Command classes derive from UserToolBoxCore bases (`UUTBBaseCommand`, `UBaseCompositeCommand`) and expose Blueprint-editable properties to configure behavior.
- Actor filters (`UBaseActorFilter` subclasses like selection, component, size filters) let commands target specific actors.
- Utility commands cover:
  - Editor actions: `UChangeViewMode`, `UZoomAll`, `UIsolateSelection`, `UShowLayersCommand`.
  - Scene ops: `UAssignToLayer`, `UAssignToLevel`, `UMirrorActorCommand`, `UFillStaticMeshActor`, `USetHighPrecisionOnMesh`, `UPushComponentMaterialIntoMesh`.
  - Execution helpers: `UExecutePythonScript`, `UExecuteBindableAction`, `UConsoleVariable`.
  - Composition: `UCompositeCommand`, `UCompositeInlineCommand`, `UToggleCommand` variants.

## 4. Typical usage patterns

- Enable UserToolBoxCore then UserToolBoxBasicCommand to get a catalog of commands in the UserToolBox asset editors.
- Create or edit a UserToolBox tab/command asset and add these command classes; configure filters (e.g., actor size or layer filters) to control scope.
- Chain multiple actions via composite commands or toggle commands to build quick editor workflows without C++.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
