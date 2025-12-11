# Wave Function Collapse (Experimental) Plugin Overview

## 1. What this plugin does

- Supplies editor tooling for tile-based model synthesis using the Wave Function Collapse (WFC) algorithm.
- Lets users define tile options and adjacency rules and then generate populated grids in the editor.
- Provides Blueprint-accessible utilities to run WFC, derive grids from scene transforms, and spawn actors/components from solved tiles.

## 2. Key Modules

- **WaveFunctionCollapse** (Editor)
  - Role: Editor subsystem, data assets, and Blueprint library for running WFC inside the editor.

## 3. Important Types & APIs

### `UWaveFunctionCollapseSubsystem` (Editor subsystem)
- Role: Owns WFC settings (model reference, grid resolution/origin/orientation) and drives the collapse process.
- Key functions (BlueprintCallable): `Collapse`, `InitializeWFC`, `Observe`, `Propagate`, `ObservationPropagation`, `DeriveGridFromTransformBounds`, and `DeriveGridFromTransforms`.

### `UWaveFunctionCollapseModel` (Data asset)
- Role: Stores tile options (`FWaveFunctionCollapseOption` with mesh/blueprint references, rotation, scale) and adjacency definitions (`EWaveFunctionCollapseAdjacency`).
- Used by the subsystem to seed possible tiles and validate constraints during observation/propagation.

### `FWaveFunctionCollapseOption` / `FWaveFunctionCollapseTile`
- Role: Represent the allowed objects per grid position and the evolving tile state during solving, including starter options and entropy tracking.

### `UWaveFunctionCollapseBPLibrary`
- Role: Blueprint library wrapper (module header) providing access to WFC functions for scripts.

## 4. Typical usage patterns

- Enable the plugin (editor-only). Create or configure a `UWaveFunctionCollapseModel` asset defining tile meshes/blueprints and adjacency rules.
- In the editor, set up `UWaveFunctionCollapseSubsystem` properties (model, resolution, origin/orientation, optional empty border) and call `Collapse` to attempt solving; adjust `TryCount`/`RandomSeed` for reproducible results.
- Use `DeriveGridFromTransformBounds` or `DeriveGridFromTransforms` to infer grid dimensions from placed actors, then run `ObservationPropagation` to complete generation.
- Successful solves can spawn actors/components for each tile via the subsystem?s spawn helpers.

## 5. Version-specific notes (UE 5.7)

- Plugin is experimental and editor-only. No explicit UE 5.7-specific behavior noted beyond the current implementation.
