# UAF State Tree Plugin Overview

## 1. What this plugin does

- Connects StateTree logic to UAF/AnimNext graphs.
- Provides traits, tasks, and conditions to run AnimNext graphs within StateTrees and exchange data.
- Includes editor and uncooked-only helpers for asset creation and compilation.

## 2. Key Modules

- **UAFStateTree** (Runtime)
  - Role: Runtime StateTree integration (traits, tasks, schema/types) for AnimNext.
- **UAFStateTreeUncookedOnly** (UncookedOnly)
  - Role: Editor-only workspace data and export helpers.
- **UAFStateTreeEditor** (Editor)
  - Role: Asset definitions, compilation handlers, factories, and editor host for AnimNext-aware StateTrees.

## 3. Important Types & APIs

### `FAnimStateTreeTrait`

- Role: Trait enabling StateTree-driven execution inside AnimNext graphs.

### StateTree tasks and conditions

- `FAnimNextStateTreeGraphInstanceTask`, `FAnimNextStateTreeRigVMTaskBase`, and `FAnimNextStateTreeRigVMConditionBase` run AnimNext graph instances or evaluate conditions from StateTree steps.

### Schemas and types

- `FAnimNextStateTreeSchema`, `FAnimNextStateTreeTypes`, and `FAnimNextStateTreeEditorOnlyTypes` define allowed data flows between StateTree and AnimNext.

### Editor helpers

- `UAnimNextStateTreeFactory`, `FAnimNextStateTreeAssetDefinition`, `FAnimNextStateTreeEditorHost`, and `FStateTreeAssetCompilationHandler` manage asset creation and compilation.

## 4. Typical usage patterns

- Author StateTree assets that reference AnimNext graphs via the provided tasks/traits to control character state logic.
- Use editor factory and asset definition to create AnimNext-aware StateTrees and compile them with the included handler.
- Workspace export helpers support editor-only data during authoring; uncooked modules are omitted from cooked builds.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
