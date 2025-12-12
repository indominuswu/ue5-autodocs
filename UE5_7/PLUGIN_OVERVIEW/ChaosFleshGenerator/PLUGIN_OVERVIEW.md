# Chaos Flesh Generator Plugin Overview

## 1. What this plugin does

- Supplies data generation tools for ML Deformer focused on Chaos Flesh simulations.
- Provides editor utilities to run flesh simulations and capture data for ML training.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor generator components (`UFleshGeneratorComponent`, `UDeformableSolverComponent`) capture Chaos Flesh data for ML Deformer training.

## 3. Key Modules

- **ChaosFleshGenerator** (Editor)  
  - Role: Editor-only module implementing flesh data generators for ML Deformer workflows.

## 4. Important Types & APIs

- `UFleshGeneratorComponent` (ChaosFleshGenerator module)  
  - Role: Component that drives flesh simulation runs for data generation.
- `UDeformableSolverComponent`, `USkeletalGeneratorComponent`  
  - Role: Supporting components used during generation to produce simulation outputs.

## 5. Typical usage patterns

- Enable when preparing ML Deformer training data for soft-body simulations.
- Add `UFleshGeneratorComponent` (and related generator components) to generation actors and run simulation scenarios to capture training data.
- Integrate outputs into ML Deformer pipelines for training or validation.

## 6. Version-specific notes (UE 5.7)

- Editor-only, disabled by default in this UE 5.7 tree, intended for ML Deformer data prep.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

