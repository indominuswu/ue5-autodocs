# Fracture Plugin Overview

## 1. What this plugin does
- Runtime support package for the Fracture Editor toolset, supplying core fracture, clustering, and geometry utility code.
- Provides fracture algorithms, sampling, convex hull generation, and material/embed helpers used when generating destructible geometry.
- Depends on the PlanarCut plugin for cutting operations.

## 2. Key Modules
- **FractureEngine** (Runtime)
  - Role: Implements fracture logic, clustering, convex decomposition, and related utilities consumed by the editor tooling.
  - Notable headers: `FractureEngineFracturing.h`, `FractureEngineClustering.h`, `FractureEngineConvex.h`, `FractureEngineSampling.h`, `FractureEngineSelection.h`, `FractureEngineMaterials.h`, `FractureEngineEmbed.h`.

## 3. Important Types & APIs

### Fracture engine utility namespaces (header groups)
- `FractureEngineFracturing`/`Clustering`/`Convex`/`Sampling` provide functions for breaking meshes, generating fracture pieces, clustering shards, and computing sampling distributions.
- `FractureEngineSelection` and `FractureEngineMaterials` help manage selection sets and material assignments on fractured results.
- `FractureEngineEmbed` and `FractureEngineUtility` contain supporting helpers used by the fracture workflow.

### `FFractureEnginePlugin`
- Role: Module definition and entry point (from `FractureEnginePlugin.h`) that exposes the fracture engine API to the editor.

## 4. Typical usage patterns
- Enable the plugin alongside the Fracture Editor tools; the runtime module supplies the algorithms invoked by the editor UI.
- Use the editor’s Fracture panel to cut and cluster geometry; underlying calls route to the functions in the `FractureEngine*` headers.
- When extending fracture behaviors, include the relevant `FractureEngine*.h` headers to call into the provided utility functions.

## 5. Version-specific notes (UE 5.7)
- Plugin is marked beta in 5.7; no additional version-specific changes detected.
