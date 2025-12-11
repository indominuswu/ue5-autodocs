# Full Body IK Plugin Overview

## 1. What this plugin does
- Provides full-body inverse kinematics solvers (Jacobian-based and Position-Based IK) for character rigs.
- Supplies Control Rig units and solver APIs to drive multi-limb IK with joint constraints and debugging options.
- Depends on Control Rig for integration with animation graphs and rigging workflows.

## 2. Key Modules
- **FullBodyIK** (Runtime)
  - Role: Full-body IK solver implementation and Control Rig units.
  - Notable types: `FRigUnit_FullbodyIK`, `FBIKConstraint`, `FBIKConstraintOption`, `FBIKDebugOption`, `FBIKConstraintLib`, `FBIKUtil`.
- **PBIK** (Runtime)
  - Role: Position-Based IK solver variant and rig units.
  - Notable types: `FRigUnit_PBIK`, `FPBIKConstraint`, `FPBIKBody`, `FPBIKSolver`, `FPBIK_Shared`.

## 3. Important Types & APIs

### `FRigUnit_FullbodyIK`
- Role: Control Rig unit that runs the full-body IK solver.
- Key properties: Effector definitions, solver iterations, convergence thresholds, per-bone constraints via `FBIKConstraint`.

### `FBIKConstraint` / `FBIKConstraintOption`
- Role: Define rotational and translational limits for joints in the solver.
- Options include stiffness, stretch limits, and per-axis toggles; `FBIKConstraintLib` exposes helper functions.

### `FPBIKSolver` and `FRigUnit_PBIK`
- Role: Position-Based IK solver and its Control Rig unit.
- Key properties: Root behavior, iteration counts, inertia/rotation limits defined in `FPBIK_Shared` and `FPBIKConstraint`.

### Debug utilities
- `FBIKDebugOption`/`PBIKDebug` headers expose draw/debug toggles for visualizing solver behavior.

## 4. Typical usage patterns
- Enable the plugin and add the provided Control Rig units (`RigUnit_FullbodyIK`, `RigUnit_PBIK`) in Control Rig graphs or animation blueprints.
- Configure constraints and effectors per limb using the constraint structs; tweak solver iteration counts and convergence settings for stability.
- Use debug options to visualize chains and constraint behavior when tuning rigs.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes discovered; plugin ships enabled for 5.7 with both FullBodyIK and PBIK solvers.
