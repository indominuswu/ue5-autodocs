# Interaction Interface Plugin Overview

## 1. What this plugin does
- Adds a gameplay interaction framework with instigator/target interfaces and components.
- Provides Blueprint helpers and an ability task to wait for nearby interaction targets.
- Integrates with Smart Objects and GameplayAbilities.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users add `InteractionInstigatorComponent`/`InteractionTargetComponent` and use `UInteractionTask_WaitForTargets`/Blueprint helpers to drive gameplay interactions.

## 3. Key Modules
- **InteractableInterface** (Runtime) - Declares interfaces, components, and tasks that power the interaction system.

## 4. Important Types & APIs
### `UInteractionInstigatorComponent` / `UInteractionTargetComponent`
- Role: Components added to instigating or target actors to participate in interactions.
- Key properties: target/instigator data (tags, ability references) for matching and activation.

### `UInteractableInstigator` / `UInteractableTargetInterface`
- Role: Interfaces defining how instigators and targets expose interaction data.

### `UInteractionTask_WaitForTargets`
- Role: Gameplay Ability task that waits for interaction targets and triggers when found.

### `UInteractableInterfaceLibrary`
- Role: Blueprint function library for querying/working with interaction targets and instigators.

## 5. Typical usage patterns
- Enable the plugin alongside SmartObjects and GameplayAbilities.
- Add `InteractionInstigatorComponent` to player/AI actors and `InteractionTargetComponent` to interactable actors.
- Use the Blueprint library or ability task to discover targets and drive interaction abilities.

## 6. Version-specific notes (UE 5.7)
- Experimental plugin; no explicit UE 5.7-only branches noted.

