# Blend Stack Plugin Overview

## 1. What this plugin does

- Blend Stack API
- Derived from plugin metadata; see source for specifics.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime exposes `FAnimNode_BlendStack` plus `UBlendStackAnimNodeLibrary` Blueprint calls (BlendTo, asset queries) for Animation Blueprints.

## 3. Key Modules

- **BlendStack** (Runtime)
- **BlendStackEditor** (UncookedOnly)

## 4. Important Types & APIs

- No major subsystem/component/settings classes were auto-detected; review source for additional APIs.

## 5. Typical usage patterns

- Enable the plugin in the project/plugins manager; modules load accordingly.
- Use the classes above in game code or Blueprints where appropriate (traits, components, subsystems, or utility libraries based on naming).
- Editor modules (if present) add supporting tooling or debugging for the runtime modules.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific or experimental notes found.

