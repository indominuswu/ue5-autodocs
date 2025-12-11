# Mover UAF Plugin Overview

## 1. What this plugin does

- Adds AnimNext/UAF integration points for the Mover movement framework.
- Provides rig units and module traits that let AnimNext graphs consume Mover trajectory data and tick ordering.
- Experimental; disabled by default.

## 2. Key Modules

- **MoverAnimNext** (Runtime) — runtime integration between Mover and AnimNext/UAF.

## 3. Important Types & APIs

- `FRigUnit_GenerateMoverTrajectory` — rig unit that queries a `UMoverComponent` to build trajectory data for animation graphs.
- `FRigVMTrait_ModuleEventDependency_MoverComponentTickFunctions` — module trait ensuring AnimNext events respect Mover component tick timing.

## 4. Typical usage patterns

- Enable alongside the core Mover plugin and AnimNext; add the rig unit in an AnimNext/UAF graph to fetch trajectories from `UMoverComponent`.
- Use the module event dependency trait to align graph execution with Mover tick order for deterministic results.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes; integration remains experimental.
