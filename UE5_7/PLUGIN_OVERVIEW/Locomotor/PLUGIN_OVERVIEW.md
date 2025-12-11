# Locomotor Plugin Overview

## 1. What this plugin does

- Experimental procedural locomotion toolkit built for Control Rig.
- Provides Rig Units and supporting math to drive foot placement, pelvis motion, and gait phase without baked animation.
- Includes debug drawing options for rapid iteration on locomotion behaviors.

## 2. Key Modules

- **Locomotor** (Runtime)
  - Role: Supplies Control Rig units and core math utilities used by locomotion rigs.
  - Notable types: `FRigUnit_Locomotor`, `FLocomotorDebugSettings`, supporting structs in `LocomotorCore.h`.

## 3. Important Types & APIs

### `FRigUnit_Locomotor`

- Role: High-level Control Rig unit that computes feet targets, body pose, and phase progression for a character.
- Key properties: Debug flags (`bDrawDebug`, `bDrawBody`, `bDrawPhaseCircle`, etc.), scaling/grounding parameters, and runtime state contained in locomotion data structs.
- Behavior: Uses spring interpolation helpers in `LocomotorCore` to smooth foot and body motion.

### Locomotor core structs/functions

- Role: Provide spring-based interpolation, plane constraints, gait phase handling, and ground alignment utilities used by the Rig Unit.
- Notable behaviors: Quaternion/vector/float spring interp helpers relying on `UKismetMathLibrary` and internal pelvis/foot update routines.

## 4. Typical usage patterns

- Enable the plugin in projects using Control Rig.
- In a Control Rig graph, add `RigUnit_Locomotor` and wire character/contact data to produce procedural foot targets and pelvis transforms.
- Use debug flags to visualize body/foot targets, collision checks, and phase circles in the viewport while tuning parameters.

## 5. Version-specific notes (UE 5.7)

- Marked as Experimental. No additional UE 5.7-specific notes found beyond its experimental status in this source tree.
