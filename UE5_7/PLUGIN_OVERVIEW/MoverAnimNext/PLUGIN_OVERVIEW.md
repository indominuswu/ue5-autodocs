# Mover UAF Plugin Overview

## 1. What this plugin does

- Adds AnimNext/UAF integration points for the Mover movement framework.
- Provides rig units and module traits that let AnimNext graphs consume Mover trajectory data and tick ordering.
- Experimental; disabled by default.

## 2. Editor/Runtime surfaces

- User-facing: Yes - AnimNext authors drop the `FRigUnit_GenerateMoverTrajectory` unit into graphs to pull trajectories from `UMoverComponent`.
- User-facing: Yes - Module event dependency trait lets users align AnimNext execution order with Mover component ticks for deterministic animation.

## 3. Key Modules

- **MoverAnimNext** (Runtime) — runtime integration between Mover and AnimNext/UAF.

## 4. Important Types & APIs

- `FRigUnit_GenerateMoverTrajectory` — rig unit that queries a `UMoverComponent` to build trajectory data for animation graphs.
- `FRigVMTrait_ModuleEventDependency_MoverComponentTickFunctions` — module trait ensuring AnimNext events respect Mover component tick timing.

## 5. Typical usage patterns

- Enable alongside the core Mover plugin and AnimNext; add the rig unit in an AnimNext/UAF graph to fetch trajectories from `UMoverComponent`.
- Use the module event dependency trait to align graph execution with Mover tick order for deterministic results.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes; integration remains experimental.

