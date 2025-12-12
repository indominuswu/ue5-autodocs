# GameplayInteractions Plugin Overview

## 1. What this plugin does
- Experimental framework for player/NPC interactions built on Smart Objects and StateTree.
- Provides interaction context data, Smart Object behavior definitions, and StateTree tasks/conditions for contextual animation and slot management.
- Supplies AI task helpers to reserve and execute gameplay interactions.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Interaction authors use the provided Smart Object behavior definition, StateTree tasks, and `UAITask_UseGameplayInteraction` to orchestrate Smart Object-driven interactions with contextual animation.

## 3. Key Modules
- **GameplayInteractionsModule** (Runtime)
  - Role: Core interaction runtime integrating Smart Objects, StateTree, and contextual animation.
  - Notable types: `FGameplayInteractionContext`, `UGameplayInteractionSmartObjectBehaviorDefinition`, `UGameplayInteractionsModule`, `UGameplayInteractionStateTreeSchema`, `UGameplayInteractionConditions`.
  - StateTree/AI helpers: `UAITask_UseGameplayInteraction`, `UStateTreeTask_PlayContextualAnim`, `UStateTreeTask_FindSlotEntranceLocation`, `UStateTreeTask_GetSlotEntranceTags`, `UStateTreeTask_PlayMontage`, `UGameplayInteractionFindSlotTask`, `UGameplayInteractionSendSlotEventTask`, `UGameplayInteractionSetSlotEnabledTask`, `UGameplayInteractionSyncSlotTagStateTask`, `UGameplayInteractionSyncSlotTagTransition`, `UGameplayInteractionListenSlotEventsTask`, `UGameplayInteractionModifySlotTagTask`, `UGameplayInteractionGetSlotActorTask`.

## 4. Important Types & APIs

### `FGameplayInteractionContext`
- Role: Struct carrying actor/slot/contextual animation references for an interaction.
- Passed through tasks and Smart Object behavior definitions to coordinate interactions.

### `UGameplayInteractionSmartObjectBehaviorDefinition`
- Role: Smart Object behavior definition that binds Smart Object use to interaction tasks defined via StateTree/contextual animations.

### AI and StateTree tasks
- `UAITask_UseGameplayInteraction` starts interaction flows from AI controllers.
- StateTree tasks handle finding slots, playing contextual animations or montages, sending slot events, enabling/disabling slots, and syncing tag state for Smart Object slots.

### `UGameplayInteractionStateTreeSchema`
- Role: StateTree schema that exposes gameplay-interaction-specific events and context to StateTree authored behaviors.

## 5. Typical usage patterns
- Enable the plugin alongside SmartObjects, StateTree, ContextualAnimation, GameplayStateTree, and NavCorridor (declared dependencies).
- Define Smart Object behavior definitions using `UGameplayInteractionSmartObjectBehaviorDefinition` and author StateTree assets that use the provided tasks.
- From AI or scripted logic, start interactions via `UAITask_UseGameplayInteraction`; StateTree tasks manage slot reservation, tag state, and animation playback.

## 6. Version-specific notes (UE 5.7)
- Plugin is experimental in 5.7. No further 5.7-specific notes were found in the current source.

