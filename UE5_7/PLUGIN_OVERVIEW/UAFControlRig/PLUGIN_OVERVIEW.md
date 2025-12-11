# UAF Control Rig Plugin Overview

## 1. What this plugin does

- Integrates Control Rig with AnimNext/UAF modules.
- Provides traits and adapters to map Control Rig hierarchies and poses into UAF graphs and tasks.
- Offers editor customization for trait properties.

## 2. Key Modules

- **UAFControlRig** (Runtime)
  - Role: Runtime Control Rig adapters, module hooks, and traits for AnimNext.
- **UAFControlRigEditor** (Editor)
  - Role: Editor customization for Control Rig traits and related properties.

## 3. Important Types & APIs

### `FAnimNextControlRigModule`

- Role: Module entry for Control Rig integration within AnimNext.

### `FAnimNextControlRigPoseAdapter` and hierarchy mappings

- Role: Adapt Control Rig pose and hierarchy data for consumption by AnimNext modules.

### `FControlRigTrait`

- Role: Trait implementation allowing Control Rig data to participate in AnimNext graph execution.
- Editor support: `FControlRigTraitCustomization` for details panel controls.

## 4. Typical usage patterns

- Add Control Rig traits to AnimNext modules to read/write Control Rig poses during graph evaluation.
- Configure hierarchy mappings to align Control Rig bones with AnimNext expectations.
- Use editor customization to tune trait properties when embedding Control Rig in UAF graphs.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
