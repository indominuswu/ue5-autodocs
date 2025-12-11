# Deformer Graph Plugin Overview

## 1. What this plugin does

- Editor for creating GPU mesh deformation graphs
- Derived from plugin metadata; see source for specifics.

## 2. Key Modules

- **OptimusSettings** (Runtime)
- **OptimusCore** (Runtime)
- **OptimusDeveloper** (UncookedOnly)
- **OptimusEditor** (Editor)

## 3. Important Types & APIs

- `UActorComponent`
- `UDebugSkelMeshComponent`
- `UMeshComponent`
- `UOptimusComponent`
- `UOptimusDeformerInstanceSettings`
- `UOptimusNode_Component`
- `UOptimusSceneComponent`
- `UOptimusSettings`
- `UOptimusSkeletalMeshComponent`
- `UOptimusSkinnedMeshComponent`
- `UPrimitiveComponent`
- `USceneComponent`
- `USkeletalMeshComponent`
- `USkinnedMeshComponent`

## 4. Typical usage patterns

- Enable the plugin in the project/plugins manager; modules load accordingly.
- Use the classes above in game code or Blueprints where appropriate (traits, components, subsystems, or utility libraries based on naming).
- Editor modules (if present) add supporting tooling or debugging for the runtime modules.

## 5. Version-specific notes (UE 5.7)

- Marked experimental/beta in metadata.
