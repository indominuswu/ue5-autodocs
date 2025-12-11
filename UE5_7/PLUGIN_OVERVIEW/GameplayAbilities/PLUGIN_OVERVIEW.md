# Gameplay Abilities Plugin Overview

## 1. What this plugin does
- Adds the Gameplay Ability System (GAS) for authoring abilities, attributes, and gameplay effects with replication and prediction support.
- Provides gameplay cues for visual/audio feedback tied to effects, plus extensive Blueprint and C++ APIs for ability logic.
- Includes editor-side helpers for authoring abilities, tags, and debugging.

## 2. Key Modules
- **GameplayAbilities** (Runtime)
  - Role: Core ability system runtime (components, effects, cues, attribute sets, tasks).
  - Notable types: `UAbilitySystemComponent`, `UGameplayAbility`, `UGameplayEffect`, `UAttributeSet`, `UAbilitySystemGlobals`, `UAbilitySystemBlueprintLibrary`, `UGameplayCueManager`, `UGameplayAbilitiesDeveloperSettings`.
- **GameplayAbilitiesEditor** (UncookedOnly)
  - Role: Editor/uncooked helpers for asset types, debugging HUDs, and validation.
  - Notable types: `AGameplayAbilityWorld`, debug HUD support, editor registration (module boilerplate).

## 3. Important Types & APIs

### `UAbilitySystemComponent`
- Role: Attachable component that owns abilities, attributes, and gameplay effects for an actor.
- Key APIs: Grant/activate abilities (`GiveAbility`, `TryActivateAbility`), apply gameplay effects (`ApplyGameplayEffectSpecToSelf/Target`), predict client ability use, register gameplay cues.

### `UGameplayAbility`
- Role: Base class for abilities (Blueprintable); defines activation policies, costs/cooldowns, input binding, and ability tasks.
- Uses `FGameplayAbilitySpec`/`FGameplayAbilitySpecHandle` for runtime instances.

### `UGameplayEffect`
- Role: Defines attribute modifications, modifiers, gameplay tags, durations, and application requirements.
- Works with `FActiveGameplayEffectHandle` for applied instances and supports attribute capture definitions.

### `UAttributeSet`
- Role: Container for gameplay attributes; integrates with gameplay effects and replication.
- Often subclassed per game to define stats; uses macros for attribute accessors.

### Gameplay cues and utilities
- `UGameplayCueManager`, `UGameplayCueNotify_Actor`, `UGameplayCueNotify_Static`, `UGameplayCueNotify_Burst` handle client/server cue dispatch.
- Blueprint helpers via `UAbilitySystemBlueprintLibrary` for effect application, tag queries, and prediction.
- Debugging: `UAbilitySystemDebugHUD`, `FGameplayDebuggerCategory_Abilities` expose runtime info.

## 4. Typical usage patterns
- Enable the plugin and add `UAbilitySystemComponent` to player/NPC actors. Define one or more `UAttributeSet` subclasses to hold stats.
- Create `UGameplayAbility` assets (Blueprint or C++) and grant them to the ability system component; bind input to trigger activations.
- Author `UGameplayEffect` assets to apply buffs/debuffs; invoke via ability tasks or blueprint library helpers.
- Implement gameplay cues (Blueprint or C++) to drive VFX/SFX when effects trigger. Use developer settings and debug HUD to inspect runtime state.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific changes surfaced; overview reflects the current 5.7 implementation of GAS.
