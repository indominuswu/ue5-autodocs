# Mutable Clothing Plugin Overview

## 1. What this plugin does
- Adds Mutable-specific helpers for working with clothing assets alongside customizable objects.
- Implements the `IMutableClothingModule` interface to adjust clothing LOD data and transition mappings.

## 2. Key Modules
- **MutableClothing** (Runtime)
  - Role: Runtime module providing clothing update hooks for Mutable-generated assets.
  - Notable types: `FMutableClothingModule` (implements `IMutableClothingModule`).

## 3. Important Types & APIs

### `FMutableClothingModule`
- Role: Module implementation that updates clothing simulation LOD data and fixes transition mappings for Mutable-driven meshes.
- Key functions: `UpdateClothSimulationLOD`, `FixLODTransitionMappings` (operate on `UClothingAssetCommon` data).

## 4. Typical usage patterns
- Enable alongside the main Mutable plugin when customizable objects include cloth.
- Allow the module to handle LOD/mapping adjustments automatically during Mutable clothing generation or updates.

## 5. Version-specific notes (UE 5.7)
- Plugin is marked experimental; no additional UE 5.7-specific notes found.
