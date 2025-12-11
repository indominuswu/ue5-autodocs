# Chaos Flesh Plugin Overview

## 1. What this plugin does

- Implements Chaos Flesh simulation for soft-body and deformable volumes.
- Provides runtime components for deformable physics, collisions, solvers, and gameplay integration.
- Adds editor tooling, asset factories, and dataflow nodes for authoring flesh assets and simulations.

## 2. Key Modules

- **ChaosFlesh** (Runtime)  
  - Role: Core Chaos Flesh simulation runtime.
- **ChaosFleshEngine** (Runtime)  
  - Role: Engine integration, components, cache adapters, and solver infrastructure.
- **ChaosFleshEditor** (Editor)  
  - Role: Editor asset factories, visualization, and authoring tools for flesh assets.
- **ChaosFleshNodes** (Runtime)  
  - Role: Dataflow nodes supporting flesh simulation workflows.
- **ChaosFleshDeprecatedNodes** (Runtime)  
  - Role: Deprecated dataflow nodes maintained for compatibility.

## 3. Important Types & APIs

- `UFleshComponent` (ChaosFleshEngine)  
  - Role: Primary component representing a flesh simulation on an actor.
- `UDeformablePhysicsComponent`, `UDeformableCollisionsComponent`, `UDeformableSolverComponent`, `UDeformableTetrahedralComponent`  
  - Role: Components composing the flesh simulation stack (physics, collisions, solver, tetrahedral mesh).
- `UChaosDeformableSolverActor`, `UChaosDeformableCollisionsActor`, `UChaosDeformableConstraintsActor`  
  - Role: Helper actors exposing billboard components and associated solver/collision components for setup and debugging.
- `FleshComponentCacheAdapter`  
  - Role: Cache adapter integrating flesh components with Chaos caching.
- Asset/data interfaces like `DIFleshDeformer`  
  - Role: Provide data to external systems (e.g., Niagara) from flesh simulations.

## 4. Typical usage patterns

- Create flesh assets and place `UFleshComponent` on actors to run Chaos Flesh simulations.
- Configure supporting components (solver, collisions, gameplay, tetrahedral mesh) to control simulation fidelity and collision behavior.
- Use editor tooling to author flesh assets and leverage dataflow nodes for pipeline customization.
- Record or play back simulations via Chaos Cache using the Flesh cache adapter when deterministic playback is needed.

## 5. Version-specific notes (UE 5.7)

- Experimental and disabled by default in this UE 5.7 build; includes deprecated dataflow nodes for compatibility.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
