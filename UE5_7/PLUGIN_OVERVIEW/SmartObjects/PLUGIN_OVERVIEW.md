# SmartObjects Plugin Overview

## 1. What this plugin does
- Provides a runtime system for placing, registering, and querying “smart objects” that AI or gameplay agents can use.
- Supports ambient life/world interaction by letting actors claim/release smart object slots and trigger behaviors.
- Includes editor tooling for authoring smart object definitions, collections, and debugging visualizers.
- Ships with test/uncooked utilities for validation.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Exposes editor authoring tools/visualizers and runtime Blueprint APIs for smart object queries and use.

## 3. Key Modules
- **SmartObjectsModule** (Runtime)
  - Role: Core runtime managing registration, reservation, and execution of smart object behaviors.
  - Notable types: `USmartObjectSubsystem`, `USmartObjectComponent`, `USmartObjectUserComponent`, `USmartObjectBlueprintFunctionLibrary`, `USmartObjectSettings`, `USmartObjectRenderingComponent`, `USmartObjectContainerRenderingComponent`.
- **SmartObjectsEditorModule** (Editor)
  - Role: Editor utilities/visualizers for smart object assets and components.
  - Notable types: `USmartObjectAssetEditorSettings`, component visualizers, asset editors.
- **SmartObjectsTestSuite** (UncookedOnly)
  - Role: Test helpers and types used by automated or sample validation of smart object flows.

## 4. Important Types & APIs
- `USmartObjectSubsystem` (UWorldSubsystem)
  - Role: Central manager tracking all smart objects in a world, handling registration, claiming, and state transitions.
  - Key functions: register/unregister definitions and runtime instances, claim/release slots for users, find smart objects via queries.
- `USmartObjectComponent` (USceneComponent)
  - Role: Placed on actors/assets to register a smart object definition in the world; supports rendering helpers.
- `USmartObjectUserComponent` (UActorComponent)
  - Role: Added to agents that will search/claim/use smart objects; communicates with the subsystem.
- `USmartObjectSettings` (UDeveloperSettings)
  - Role: Project-level configuration for the smart object system (e.g., trace channels, debug settings).
- `USmartObjectBlueprintFunctionLibrary`
  - Role: Blueprint helpers to locate, claim, and interact with smart objects at runtime.
- `USmartObjectPersistentCollection`
  - Role: Asset/actor that stores a collection of smart objects for a level; supports container rendering and debug drawing.
- Debug components (`USmartObjectDebugRenderingComponent`, `USmartObjectContainerRenderingComponent`, `USmartObjectSubsystemRenderingComponent`)
  - Role: Visualize registered objects, slots, and claims during development.

## 5. Typical usage patterns
- Enable the SmartObjects plugin and its dependencies (GameplayAbilities, TargetingSystem, WorldConditions).
- Author smart object definitions and place actors with `USmartObjectComponent`, or create `USmartObjectPersistentCollection` assets for level-wide registration.
- Add `USmartObjectUserComponent` to AI/agents; at runtime, query `USmartObjectSubsystem` or use Blueprint library functions to find and claim available smart object slots.
- Use the editor module’s visualizers and debug rendering components to inspect placements and reservations during play-in-editor.
- For testing, rely on the provided test suite utilities in non-cooked builds.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
