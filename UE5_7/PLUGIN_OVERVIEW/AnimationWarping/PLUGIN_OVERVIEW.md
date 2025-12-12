# Animation Warping Plugin Overview

## 1. What this plugin does

- Framework for animation and pose warping. This plugin includes Stride, Orientation, and Slope Warping alongside the Root Motion Delta animation attribute.
- Derived from plugin metadata; see source for specifics.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime warping framework (Stride/Orientation/Slope) with an editor module supporting animation authoring/debugging.

## 3. Key Modules

- **AnimationWarpingRuntime** (Runtime)
- **AnimationWarpingEditor** (UncookedOnly)

## 4. Important Types & APIs

- `UCharacterMovementComponent`
- `USkeletalMeshComponent`

## 5. Typical usage patterns

- Enable the plugin in the project/plugins manager; modules load accordingly.
- Use the classes above in game code or Blueprints where appropriate (traits, components, subsystems, or utility libraries based on naming).
- Editor modules (if present) add supporting tooling or debugging for the runtime modules.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific or experimental notes found.
