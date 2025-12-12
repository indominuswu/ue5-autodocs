# ControlRigPhysics Plugin Overview

## 1. What this plugin does

- Adds physics simulation support to Control Rig hierarchies, enabling dynamic bodies and joints inside rigs.
- Provides rig components and execution units to drive physics bodies, collision, and solver settings per rig element.
- Intended for experimental physicalized rig workflows rather than full character physics.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Runtime Control Rig extension exposing physics body components/rig units that authors add to rigs to simulate dynamics and collisions.

## 3. Key Modules

- **ControlRigPhysics** (Runtime)  
  - Role: Physics body definitions, solver data, and rig execution helpers for Control Rig graphs.
  - Notable types: `FRigPhysicsBodyComponent`, `FRigPhysicsBodySolverSettings`, `FRigPhysicsBodyExecution`.

## 4. Important Types & APIs

### `FRigPhysicsBodyComponent`
- Role: Rig component describing a physical body attached to a hierarchy element, including dynamics and collision data.
- Key properties: `BodySolverSettings`, `Dynamics`, `Collision`, `BodyData`, `KinematicTarget`, `NoCollisionBodies`.
- Key functions: `AutoCalculateCollision`, overrides for save/load, icon lookup, and hierarchy key change handling.

### `FRigPhysicsBodyExecution`
- Role: Execution helper for applying physics simulation to rig bodies during graph evaluation.
- Key behavior: Bridges rig VM execution with physics control data.

### `RigPhysics` data structures
- Role: Shared physics configuration (e.g., `FRigPhysicsData`, solver modifiers) used by components and execution nodes.

## 5. Typical usage patterns

- Enable the plugin for Control Rig assets that need lightweight physics-driven elements.
- Add physics body components to rig elements and configure solver, collision, and control data.
- Use execution units supplied by the plugin inside Control Rig graphs to advance simulation or sync kinematic targets.
- For editor workflows, tweak collision generation (`AutoCalculateCollision`) and solver settings per body.

## 6. Version-specific notes (UE 5.7)

- Marked experimental; no explicit 5.7-only changes documented in source comments.

