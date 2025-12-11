# Gameplay Abilities Game Feature Actions Plugin Overview

## 1. What this plugin does
- Adds a `UGameFeatureAction` that injects Gameplay Ability System attribute default tables when a Game Feature is registered or activated.
- Lets modular game features push and remove attribute defaults without touching project settings.
- Designed for GAS-driven projects that split content into feature plugins.

## 2. Key Modules
- **AbilitySystemGameFeatureActions** (Runtime)
  - Role: Provides the game feature action that applies/removes attribute default tables during the feature lifecycle.

## 3. Important Types & APIs

### `UGameFeatureAction_AddAttributeDefaults`
- Role: On registration/activation, adds attribute default tables owned by the game feature; removes them on deactivation/unregister.
- Key properties: `bApplyOnRegister` (apply at register vs. activate), `AttribDefaultTableNames` (soft object paths to default tables).
- Lifecycle hooks: Overrides `OnGameFeatureRegistering/Activating/Deactivating/Unregistering` to push/pull defaults; editor support via `PostEditChangeProperty`.

## 4. Typical usage patterns
- Add this action to a Game Feature plugin definition to supply ability attribute defaults with that feature.
- Populate `AttribDefaultTableNames` with data tables containing GAS attribute defaults.
- Choose whether defaults are applied on register or activation using `bApplyOnRegister`.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.