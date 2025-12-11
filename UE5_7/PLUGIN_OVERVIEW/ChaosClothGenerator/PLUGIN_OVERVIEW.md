# Chaos Cloth Generator Plugin Overview

## 1. What this plugin does

- Adds data generation utilities for ML Deformer that target Chaos Cloth simulations.
- Provides an editor module to generate cloth simulation data for training or testing deformers.

## 2. Key Modules

- **ChaosClothGenerator** (Editor)  
  - Role: Editor-only tools for generating Chaos cloth data sets for ML Deformer workflows.

## 3. Important Types & APIs

- `UClothGeneratorComponent` / `UChaosClothComponent` (ChaosClothGenerator module)  
  - Role: Component used during generation to run cloth simulations and capture data for ML pipelines.

## 4. Typical usage patterns

- Enable when preparing ML Deformer training data for cloth.  
  - Add `UClothGeneratorComponent` to actors in generation maps to simulate cloth and collect outputs.
- Use the provided editor utilities to automate cloth simulation runs and gather data for ML training.

## 5. Version-specific notes (UE 5.7)

- Editor-only plugin with no default enablement in this 5.7 tree.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
