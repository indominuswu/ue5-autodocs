# Planar Cut Plugin Overview

## 1. What this plugin does

- Runtime helpers for performing planar cuts on meshes and Geometry Collections.
- Provides support code for fracturing workflows (Chaos/Fracture) including noise-based surface perturbation and automatic UV generation for cut faces.
- Supplies reusable math/utility structs (e.g., planar cell generation, internal surface material data) for other tools to build on.
- Experimental; off by default.

## 2. Key Modules

- **PlanarCut** (Runtime)  
  - Role: Core geometry utilities for building planar cells, applying Voronoi/box/voxel-based cuts, adding noise, and baking UVs on new faces.
  - Notable types: `FPlanarCells`, `FNoiseSettings`, `FInternalSurfaceMaterials`, UV helpers in `FractureAutoUV.h`, math in `GeometryMeshConversion.h`.

## 3. Important Types & APIs

### `FPlanarCells`

- Role: Represents planes and boundaries used to slice meshes/Geometry Collections (single plane, Voronoi sites, boxes, grids, or images).
- Key properties: `Planes`, `PlaneCells`, `PlaneBoundaries`, `PlaneBoundaryVertices`, `AssumeConvexCells`, `InternalSurfaceMaterials`.
- Key functions: Constructors for different cell sources; `DiscardCells` to cull subsets; validation helpers for plane boundary orientation.

### `FNoiseSettings` / `FNoiseOffsets`

- Role: Configures Perlin noise amplitude/frequency/octaves for perturbing cut surfaces.
- Key properties: `Amplitude`, `Frequency`, `Octaves`, `PointSpacing`, `Lacunarity`, `Persistence`; helper `NoiseVector`/`OctaveNoise`.

### UV helpers in `FractureAutoUV`

- Role: Generate/bake UVs for newly exposed geometry after cutting.
- Key pieces: `FMergeIslandSettings`, `FTextureAttributeSettings`, `SetUVScaleFromCollection` helpers to derive UV scale from Geometry Collection data.

## 4. Typical usage patterns

- Editor tools that fracture meshes (e.g., Chaos/Fracture workflows) call into these APIs to compute cutting planes and bake UVs; there are no Blueprint nodes or actor components exposed directly.
- Integrate by including `PlanarCut` in your module and using the helper structs/functions to generate cell definitions, apply noise, and convert the results back into meshes/Geometry Collections.
- Material handling helpers (`FInternalSurfaceMaterials`) allow callers to set default material IDs and optional UV scaling for interior faces.

## 5. Version-specific notes (UE 5.7)

- Marked as experimental and disabled by default in UE 5.7.
- No explicit 5.7-only APIs were noted; overview reflects the current source state.
