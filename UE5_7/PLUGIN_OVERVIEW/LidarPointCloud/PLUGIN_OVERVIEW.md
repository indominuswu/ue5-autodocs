# LiDAR Point Cloud Support Plugin Overview

## 1. What this plugin does
- Imports, processes, and renders LiDAR point clouds within Unreal.
- Provides runtime components and actors for querying, coloring, culling, and editing point cloud data.
- Includes editor tools (factories, modes, toolkits) to import LiDAR formats and interactively edit point sets.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor import/edit modes plus runtime actors/components and Blueprint-accessible point cloud queries.

## 3. Key Modules
- **LidarPointCloudRuntime** (Runtime)  
  - Role: Core point cloud asset/component implementation and runtime queries.
  - Notable types: `ULidarPointCloud`, `ULidarPointCloudComponent`, `ALidarPointCloudActor`, `ULidarPointCloudSettings`, `ULidarPointCloudLODManager`.
- **LidarPointCloudEditor** (Editor)  
  - Role: Import/edit tooling and viewport interaction.
  - Notable types: `ULidarPointCloudFactory`, `ActorFactoryLidarPointCloud`, `FLidarPointCloudEdMode`, `FLidarPointCloudEdModeToolkit`.

## 4. Important Types & APIs

### `ULidarPointCloudComponent`
- Role: Renders and manipulates sections of a point cloud.
- Key properties: `PointCloud` asset reference, `PointSize`, `ScalingMethod`, `GapFillingStrength`, coloration settings (classification/elevation/tint), culling options (`MinDepth`, `MaxDepth`, frustum culling).
- Key functions: Spatial queries (`HasPointsInSphere/Box/Ray`), gather points (`GetPointsInSphere/BoxAsCopies`, `LineTraceMulti`), edit visibility (`SetVisibilityOfPoints*`), color edits (`ApplyColorToPoints*`), point removal, and selection utilities (editor).

### `ULidarPointCloud`
- Role: Asset storing octree-based point data with file IO helpers (LAS, E57, ASCII) and meshing/rendering utilities.
- Used internally by the component for queries and rendering.

### Editor tooling
- `ULidarPointCloudFactory` imports common LiDAR formats.
- `FLidarPointCloudEdMode` and toolkit provide in-editor selection/painting/cleanup tools for point data.

## 5. Typical usage patterns
- Import LiDAR data via the factory, then place an `ALidarPointCloudActor` or add a `ULidarPointCloudComponent` to an actor.
- Configure appearance (size, coloration, orientation) and perform spatial queries or raycasts in Blueprints/C++ for gameplay or analysis.
- Editor: Use the LiDAR Point Cloud edit mode to select, recolor, hide, or remove points; use ActorFactory to quickly create actors from assets.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; functionality is based on the current runtime/editor modules in this engine version.
