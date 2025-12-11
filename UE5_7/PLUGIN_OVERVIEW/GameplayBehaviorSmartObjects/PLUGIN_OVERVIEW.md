# GameplayBehaviorSmartObjects Plugin Overview

## 1. What this plugin does
- Experimental Smart Objects extension that uses `UGameplayBehavior` as the default runtime behavior for Smart Object interactions.
- Adds behavior definitions, AI tasks, and Blueprint helpers tailored to Smart Object usage.
- Relies on the GameplayBehaviors and SmartObjects plugins.

## 2. Key Modules
- **GameplayBehaviorSmartObjectsModule** (Runtime)
  - Role: Registers Smart Object behavior definitions, AI/BT tasks, and blueprint helpers to drive behaviors through Smart Objects.
  - Notable types: `UGameplayBehaviorSmartObjectBehaviorDefinition`, `UGameplayBehaviorSmartObjectsBlueprintFunctionLibrary`, `UAITask_UseGameplayBehaviorSmartObject`, `UBTTask_FindAndUseGameplayBehaviorSmartObject`.

## 3. Important Types & APIs

### `UGameplayBehaviorSmartObjectBehaviorDefinition`
- Role: Smart Object behavior definition that wraps a `UGameplayBehavior` to run when the Smart Object is used.

### `UAITask_UseGameplayBehaviorSmartObject`
- Role: AI task that reserves and uses a Smart Object slot, running the associated gameplay behavior on the AI actor.
- Supports typical AI task lifecycle (activate, tick, end) for behavior-driven interactions.

### `UBTTask_FindAndUseGameplayBehaviorSmartObject`
- Role: Behavior tree task to locate an appropriate Smart Object and run its gameplay behavior via AI task.

### `UGameplayBehaviorSmartObjectsBlueprintFunctionLibrary`
- Role: Blueprint helpers for issuing Smart Object use requests backed by gameplay behaviors.

## 4. Typical usage patterns
- Enable GameplayBehaviors, SmartObjects, and this plugin.
- Author Smart Object definitions that reference `UGameplayBehaviorSmartObjectBehaviorDefinition` to map to a specific gameplay behavior asset.
- From AI controllers, call the Blueprint function library or use `UAITask_UseGameplayBehaviorSmartObject` / `UBTTask_FindAndUseGameplayBehaviorSmartObject` to reserve and run Smart Objects.

## 5. Version-specific notes (UE 5.7)
- Plugin marked experimental in 5.7; no additional version-specific notes observed.
