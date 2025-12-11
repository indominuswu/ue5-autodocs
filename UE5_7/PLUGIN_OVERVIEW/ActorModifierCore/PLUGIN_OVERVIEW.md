# Actor Modifier Core Plugin Overview

## 1. What this plugin does
- Provides the core framework for applying reusable "modifiers" to actors, defining behavior adjustments via shared objects/components.
- Supplies base classes, subsystem support, and Blueprint types for creating and stacking modifiers.
- Editor tooling for authoring modifier assets and profiling their execution.

## 2. Key Modules
- **ActorModifierCore** (Runtime)
  - Role: Core runtime types (components, stacks, shared objects) that apply modifier logic to actors.
- **ActorModifierCoreBlueprint** (UncookedOnly)
  - Role: Blueprint support for authoring modifier logic and assets.
- **ActorModifierCoreEditor** (Editor)
  - Role: Editor menus, detail customizations, Blueprint factories, and profiler UI for modifier assets.

## 3. Important Types & APIs

### `UActorModifierCoreComponent`
- Role: Component that owns and executes modifier stacks on an actor.
- Key responsibilities: manage modifier instances, initialize shared actors/objects, coordinate execution order.

### `UActorModifierCoreStack`
- Role: Represents an ordered stack of modifier entries applied to an actor/component.
- Behavior: Handles creation, removal, and evaluation of modifiers in sequence.

### `UActorModifierCoreBlueprintBase` / `UActorModifierCoreBlueprint`
- Role: Base Blueprintable classes for defining custom modifiers without C++.
- Key properties: metadata/definitions that describe modifier behavior and exposed parameters.

### `UActorModifierCoreSubsystem`
- Role: Engine subsystem managing modifier assets and providing utility access.

### `UActorModifierCoreSharedObject` / `UActorModifierCoreSharedActor`
- Role: Shared context objects/actors accessible across modifiers in a stack.

### Editor types
- Factories and asset definitions (e.g., `UActorModifierCoreBlueprintFactory`, `AssetDefinition_ActorModifierCoreBlueprint`) enable creating modifier assets.
- Editor UI classes (`SActorModifierCoreEditorProfiler`, `UActorModifierCoreEditorSubsystem`) support profiling and customization.

## 4. Typical usage patterns
- Add an `UActorModifierCoreComponent` to actors that should host modifier stacks.
- Create modifier assets (Blueprint or C++) deriving from `UActorModifierCoreBlueprintBase`, then assign them to stacks.
- Use the Editor module tools to create, edit, and profile modifier setups; use shared objects/actors to pass data between modifiers.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.