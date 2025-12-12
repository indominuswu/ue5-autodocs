# Chaos Cloth Plugin Overview

## 1. What this plugin does

- Provides Chaos-based cloth simulation modules for runtime cloth behavior.
- Supplies editor hooks for cloth simulation visualization and setup.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users configure Chaos cloth on skeletal meshes and use editor visualization/setup tools; runtime cloth simulation is part of gameplay.

## 3. Key Modules

- **ChaosCloth** (Runtime)  
  - Role: Core Chaos cloth simulation runtime for skinned meshes and skeletal mesh components.
- **ChaosClothEditor** (Editor)  
  - Role: Editor extensions for cloth simulation configuration and visualization within skeletal mesh editors.

## 4. Important Types & APIs

- `FChaosClothingSimulation`, `FChaosClothingSimulationSolver` (ChaosCloth module)  
  - Role: Core simulation classes integrating cloth with `USkeletalMeshComponent` / `USkinnedMeshComponent`.
- `FChaosClothingSimulationCollider`, `FChaosClothingSimulationSkeletalMesh`  
  - Role: Collider and mesh support for Chaos cloth simulations.
- Editor extenders in `ChaosClothEditor` module register simulation visualization with skeletal mesh editors.

## 5. Typical usage patterns

- Enable Chaos Cloth to run cloth simulations on skeletal meshes using the Chaos solver.
- Configure cloth assets via skeletal mesh clothing data; editor module provides visualization and setup tools.
- At runtime, cloth attaches to `USkeletalMeshComponent` with Chaos simulation running through the plugin.

## 6. Version-specific notes (UE 5.7)

- Enabled by default in this 5.7 tree as the Chaos cloth solution.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

