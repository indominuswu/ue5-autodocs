# Unreal Animation Framework (UAF) Plugin Overview

## 1. What this plugin does

- Provides the core AnimNext/UAF runtime for defining functional data-flow animation modules.
- Supplies world subsystems, module instances, RigVM traits, and execution contexts used by other UAF integrations.
- Disabled by default and marked experimental under the Animation category.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Exposes AnimNext runtime/Blueprint-RigVM integration and editor support for authoring UAF modules.

## 3. Key Modules

- **UAF** (Runtime)
  - Role: Core runtime for AnimNext modules, execution contexts, and world integration.
- **UAFEditor** (Editor)
  - Role: Editor-facing support for AnimNext assets and tooling (e.g., RigVM integration and debug draw).
- **UAFUncookedOnly** (UncookedOnly)
  - Role: Editor-only data/authoring helpers that do not cook.
- **UAFTestSuite** (UncookedOnly)
  - Role: Automated test coverage for the framework.

## 4. Important Types & APIs

### `UAnimNextWorldSubsystem`

- Role: World subsystem that owns AnimNext module execution, tick bindings, and pooled data structures.

### Module/runtime infrastructure

- `FAnimNextModule`, `FAnimNextModuleInstance`, `FAnimNextModuleContextData` manage module construction, context data, and tick execution.
- `FAnimNextExecuteContext` and `FRigUnit_AnimNextBeginExecution` define the entry for AnimNext RigVM graphs.
- Trait and parameter helpers (`AnimNextModuleEventTickFunctionBindings`, `AnimNextActorComponentReferenceComponent`, locator fragments) route actors/components/object properties into modules.

### RigVM/graph support

- `RigUnit_AnimNextModuleEvents`, `RigUnit_AnimNextModuleEventDependencies`, `RigUnit_AnimNextTraitStack` expose module events and traits inside RigVM graphs.

## 5. Typical usage patterns

- Enable UAF and author AnimNext graphs/modules; the world subsystem initializes module instances and ticks them alongside actors.
- Use locator fragments and trait stacks to bind actor/components into animation graphs and route data through modules.
- Combine with other UAF integrations (AnimGraph, Control Rig, Pose Search, StateTree, etc.) to drive complex animation behaviors.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
