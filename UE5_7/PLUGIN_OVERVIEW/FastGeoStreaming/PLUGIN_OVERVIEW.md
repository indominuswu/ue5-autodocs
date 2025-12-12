# FastGeo Streaming Plugin Overview

## 1. What this plugin does
- Experimental system that converts partitioned world geometry into simplified, streamable representations to improve runtime streaming performance.
- Supplies specialized mesh component types for static, instanced, procedural, skinned, and HLOD elements optimized for FastGeo containers.
- Provides a world subsystem and runtime cell transformer to manage FastGeo data within World Partition.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers enable this experimental FastGeo workflow, run extraction for World Partition data, and use FastGeo mesh components/subsystems to stream optimized geometry at runtime.

## 3. Key Modules
- **FastGeoStreaming** (Runtime, Experimental)
  - Role: Core runtime for FastGeo extraction, container management, and streaming.
  - Notable types: `UFastGeoWorldSubsystem`, `UFastGeoWorldPartitionRuntimeCellTransformer`, `UFastGeoPrimitiveComponent` family.

## 4. Important Types & APIs

### `UFastGeoWorldSubsystem`
- Role: World subsystem coordinating FastGeo streaming tasks and lifecycle within a world.
- Interacts with partitioned world data and FastGeo containers to stage streamable geometry.

### `UFastGeoWorldPartitionRuntimeCellTransformer`
- Role: Transforms World Partition runtime cells into FastGeo-ready payloads.
- Helps translate partitioned content into clustered FastGeo components for streaming.

### FastGeo component family
- Roles: Specialized component implementations (e.g., `UFastGeoStaticMeshComponent`, `UFastGeoInstancedStaticMeshComponent`, `UFastGeoInstancedSkinnedMeshComponent`, `UFastGeoProceduralISMComponent`, `UFastGeoSkinnedMeshComponent`, `UFastGeoHLOD`) that hold FastGeo element data and render/stream accordingly.
- Supporting structures: `FFastGeoContainer`, `FFastGeoComponentCluster`, `FFastGeoWeakElement`, and interfaces like `IFastGeoElement`.

### `FFastGeoAsyncRenderStateJobQueue`
- Role: Manages async jobs related to render state updates for FastGeo elements.

## 5. Typical usage patterns
- Enable the experimental plugin for projects using World Partition that need optimized geometry streaming.
- Run the FastGeo extraction workflow (code-driven) to convert partitioned world content into FastGeo containers; the world subsystem manages their streaming at runtime.
- Use the specialized FastGeo component types in place of standard mesh components when authoring or generating FastGeo representations.

## 6. Version-specific notes (UE 5.7)
- Marked Experimental in 5.7; no additional UE 5.7-specific flags beyond the experimental status were identified.

