# Targeting System Plugin Overview

## 1. What this plugin does
- Experimental, generic targeting framework for gameplay (aim assist, ability targeting, etc.).
- Provides targeting presets, tasks (selection/filter/sort), and async/ability tasks for driving targeting flows.
- Integrates with GameplayAbilities for ability task support.

## 2. Key Modules
- **TargetingSystem** (Runtime)
  - Role: Core targeting data structures, tasks, presets, subsystem, and async/ability tasks.
  - Notable types: `UTargetingSubsystem`, `UTargetingPreset`, tasks under `Tasks/` (selection, filter, sort), async helpers (`AsyncAction_PerformTargeting`, `AbilityTask_PerformTargeting`).

## 3. Important Types & APIs
### `UTargetingSubsystem`
- Role: Central subsystem executing targeting requests and managing data stores (`TargetingSystemDataStores`).
- Key functions: run targeting queries using presets and task chains; expose delegates/results.

### `UTargetingPreset`
- Role: Defines a sequence of targeting tasks (selection, filtering, sorting) for reuse.

### Targeting tasks (e.g., `TargetingSelectionTask_Trace`, `TargetingSelectionTask_AOE`, `TargetingFilterTask_ActorClass`, `TargetingFilterTask_SortByDistance`, `SimpleTargetingSelectionTask`, `SimpleTargetingFilterTask`, `SimpleTargetingSortTask`)
- Role: Building blocks for composing targeting pipelines; perform traces/AOE collection, filter by class or distance, sort results.

### `AsyncAction_PerformTargeting` / `AbilityTask_PerformTargeting`
- Role: Blueprint and GameplayAbility tasks to kick off targeting flows asynchronously and return results.

### `CollisionQueryTaskData`, `TargetingSystemTypes`
- Role: Shared data/config structures passed between tasks.

## 4. Typical usage patterns
- Enable the plugin (depends on GameplayAbilities).
- Create a `UTargetingPreset` asset or data object specifying selection/filter/sort tasks.
- From gameplay code/Blueprint, call `AsyncAction_PerformTargeting` or `AbilityTask_PerformTargeting` to run the preset; bind to completion to get target data.
- Customize tasks or data stores to fit game-specific targeting rules.

## 5. Version-specific notes (UE 5.7)
- Marked beta/experimental in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
