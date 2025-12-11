# Tet Meshing Plugin Overview

## 1. What this plugin does

- Adds experimental support for generating and refining tetrahedral meshes.
- Provides utilities for building tetra meshes from primitives or isosurfaces (e.g., via stuffing approaches).
- Designed for physics/geometry workflows; disabled by default.

## 2. Key Modules

- **TetMeshing** (Runtime)
  - Role: Hosts tetrahedral mesh generation utilities and logging.

## 3. Important Types & APIs

### `ITetMeshingPlugin`

- Role: Runtime module interface exposing `Get()`/`IsAvailable()` helpers to load the module on demand.

### `TTetMeshGenerator`

- Role: Template base class that accumulates tetra vertices, indices, optional triangle faces, and IDs and exposes a `Generate()` entry point for subclasses.
- Key properties: `Vertices`, `Tets`, `Triangles`, optional ID arrays, and `bReverseOrientation`.

### `FIsosurfaceStuffing` (in `IsosurfaceStuffing.h`)

- Role: Utilities for tetrahedralizing isosurfaces; supplies algorithms used by concrete generators.

## 4. Typical usage patterns

- Include the TetMeshing headers in C++ and construct a generator derived from `TTetMeshGenerator` (or use the provided stuffing helpers) to build tetra meshes from geometry or volume data.
- No editor UI is provided; consumption is via C++ utilities and data structures.
- Marked experimental; expect API changes.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
