# Proxy LOD Plugin (Experimental) Overview

## 1. What this plugin does
- Provides tools to generate proxy LOD meshes using mesh simplification, partitioning, and material baking utilities.
- Intended for editor workflows such as HLOD generation or aggressive mesh reduction for large worlds.
- Leverages third-party code (DirectXMesh, UVAtlas) for mesh processing and parameterization.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor-facing proxy/HLOD reduction APIs (`IProxyLODPlugin`, mesh reduction/material transfer helpers) used by HLOD builders and mesh simplification tools.

## 3. Key Modules
- **ProxyLODMeshReduction** (Editor)  
  - Role: Mesh reduction and proxy generation algorithms plus supporting math/utilities.  
  - Notable types: `IProxyLODPlugin` interface, numerous helpers (`ProxyLODMeshUtilities`, `ProxyLODSimplifier`, `ProxyLODParallelSimplifier`, `ProxyLODMeshPartition`, `ProxyLODMaterialTransferUtilities`).

## 4. Important Types & APIs
### `IProxyLODPlugin`
- Role: Module interface used to access proxy LOD generation services from editor tooling.

### Mesh/utility helpers
- Role: Functions for rasterization, quadric error simplification, material transfer, grid/partitioning, and SDF conversions (`ProxyLODMeshUtilities`, `ProxyLODQuadric`, `ProxyLODRasterizer`, `ProxyLODMeshSDFConversions`).

## 5. Typical usage patterns
- Enable the experimental plugin and invoke proxy/HLOD generation tools that call into `ProxyLODMeshReduction`.
- Configure reduction settings (partitioning, simplification quality, material transfer) through the calling tool or HLOD builder using this module.
- Outputs simplified proxy meshes and baked material data suitable for HLOD or distant LODs.

## 6. Version-specific notes (UE 5.7)
- Marked beta/experimental and Win64-only per the descriptor; no additional UE 5.7-specific notes found.

