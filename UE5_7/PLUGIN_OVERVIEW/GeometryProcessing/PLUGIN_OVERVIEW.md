# Geometry Processing Plugin Overview

## 1. What this plugin does

- Supplies foundational geometry algorithms and Dynamic Mesh utilities used by modeling, mesh processing, and baking tools.
- Provides math/geometry libraries (GTEngine, xatlas, fTetWild) wrapped by Unreal modules for remeshing, UVs, simplification, and sampling.
- Offers helper utilities for mesh file IO and algorithm wrappers used by higher-level plugins (e.g., Modeling Tools, Geometry Scripting).

## 2. Key Modules

- **GeometryAlgorithms** (Runtime)  
  - Role: Core geometric algorithms (fTetWild wrappers, xatlas UV packing, PCA, convex hulls, fitting, arrangement, Clipper-based polygon ops).  
  - Notable types: `FGeometryAlgorithmsModule`, `Arrangement2d`, `ConstrainedDelaunay2`, `FTetWildWrapper`, `XAtlasWrapper`, `MinVolumeBox3`, `MinVolumeSphere3`.

- **DynamicMesh** (Runtime)  
  - Role: Dynamic mesh data structures and operations (remeshing, smoothing, UV editors, mesh bakers, shape approximation, solvers).  
  - Notable types: `FDynamicMeshUVEditor`, `FRemesher`, `FMeshSimplification`, `FMeshRegionOperator`, `MeshPlaneCut`, `MeshNormals`, `MeshTangents`, `MeshBaker` utilities, `GeometrySelection`.

- **MeshFileUtils** (DeveloperTool)  
  - Role: Lightweight helpers for mesh file parsing/export.  
  - Notable types: `FMeshFileUtilsModule`, `OBJMeshUtil`.

## 3. Important Types & APIs

### Dynamic Mesh operations

- Role: Classes and utilities for editing/remeshing meshes at runtime or in tools (`ExtrudeMesh`, `Remesher`, `MeshBevel`, `MeshSimplify`, `MeshProjectionHull`, `MeshUVPacking`, `MeshSurfaceSampler`).
- Key inputs: `FDynamicMesh3`/attribute data plus per-operation settings for tolerances, iteration counts, and target counts.

### Solvers and parameterization

- Role: Linear system/Poisson/Laplacian solvers (`ConstrainedMeshDeformationSolver`, `MeshParameterizationSolvers`, `MeshDiffusionSmoothing`) and UV editors (`FDynamicMeshUVEditor`, `PatchBasedMeshUVGenerator`).

### Sampling and baking utilities

- Role: `MeshMapBaker`, `MeshNormalMapBaker`, `MeshCurvatureMapBaker`, `MeshOcclusionMapBaker` for generating texture maps from mesh data.

### Geometry algorithms

- Role: Wrappers for convex hulls, minimum volume shapes, PCA, Clipper polygon ops, Delaunay triangulation, and xatlas UV packing.

## 4. Typical usage patterns

- Used by higher-level plugins (Modeling Tools, Geometry Scripting, GeometryFlow) to perform mesh edits, remeshing, UV generation, and baking.
- Game/runtime code can link against these modules to perform custom geometry processing tasks using the Dynamic Mesh APIs.
- MeshFileUtils can be used to parse/export simple mesh data (e.g., OBJ) for tool pipelines.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
