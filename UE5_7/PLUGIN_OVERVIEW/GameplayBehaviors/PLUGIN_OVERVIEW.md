# AI Behaviors Plugin Overview

## 1. What this plugin does
- Experimental framework for encapsulated, fire-and-forget AI behaviors.
- Provides behavior assets/configs that can be triggered on AI actors without fully authored behavior trees.
- Adds behavior tree helpers and a subsystem to manage active behaviors.
- Includes an editor module for styling and registration.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime behavior subsystem/assets and BT helpers, plus editor styling/registration support.

## 3. Key Modules
- **GameplayBehaviorsModule** (Runtime & UncookedOnly)
  - Role: Core behavior runtime plus uncooked support for packaging.
  - Notable types: `UGameplayBehavior`, `UGameplayBehaviorConfig`, `UGameplayBehavior_AnimationBased`, `UGameplayBehavior_BehaviorTree`, `UGameplayBehaviorSubsystem`, `UGameplayBehaviorsBlueprintFunctionLibrary`, Blackboard/BT helpers (`UBTDecorator_GameplayTagQuery`, `UBTTask_StopGameplayBehavior`, `UBTTask_SetKeyValueGameplayTag`), tag utilities (`UValueOrBBKey_GameplayTag`).
- **GameplayBehaviorsEditorModule** (Editor)
  - Role: Editor registration and styling.
  - Notable types: `FGameplayBehaviorsEditorModule`, `FGameplayBehaviorsEditorStyle`.
- **GameplayBehaviorsTestSuite** (Runtime test support)
  - Role: Test suite module wrapper (`FGameplayBehaviorsTestSuiteModule`) for automated testing.

## 4. Important Types & APIs

### `UGameplayBehavior`
- Role: Base class for behaviors that can be activated on AI actors.
- Supports activation requests, optional instancing, and tag-based requirements.

### `UGameplayBehaviorConfig` and derived configs
- Role: Config assets that describe how to run a behavior (animation-based, behavior tree-based, etc.).
- Provide serialized settings consumed when activating behaviors.

### `UGameplayBehaviorSubsystem`
- Role: Subsystem that tracks and dispatches active behaviors for a world.
- Exposes activation and stopping APIs used by behavior tree tasks and gameplay systems.

### AI helpers
- Behavior tree decorator/task classes to gate and trigger behaviors using gameplay tags and to stop behaviors when needed.
- Blueprint library (`UGameplayBehaviorsBlueprintFunctionLibrary`) to start/stop/query behaviors in Blueprints.

## 5. Typical usage patterns
- Enable the plugin (experimental) and create behavior/config assets derived from `UGameplayBehavior` and `UGameplayBehaviorConfig_*`.
- From AI logic (behavior trees or Blueprint), trigger behaviors via the blueprint library or provided BT tasks; the subsystem manages execution.
- Use tag-based decorators (`UBTDecorator_GameplayTagQuery`) and tasks (`UBTTask_SetKeyValueGameplayTag`) to coordinate behavior activation based on gameplay tag state.

## 6. Version-specific notes (UE 5.7)
- Plugin marked beta/experimental in 5.7. No other 5.7-specific changes were identified.
