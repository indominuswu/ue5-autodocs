# Dataprep Geometry Operations Plugin Overview

## 1. What this plugin does

- Adds experimental geometry processing operations usable inside the Dataprep Editor.
- Provides filters and transforms for geometry cleanup tasks (e.g., jacketing and selection transforms).
- Extends Dataprep with additional geometry-focused steps.

## 2. Key Modules

- **DataprepGeometryOperations** (Editor)  
  - Role: Editor-only library of geometry operations.
  - Notable types: `DataprepGeometryOperations`, `DataprepGeometryFilters`, `DataprepGeometrySelectionTransforms`, `FJacketingProcess`.

## 3. Important Types & APIs

### `DataprepGeometryOperations`
- Role: Collection of geometry operations exposed to Dataprep pipelines.
- Key behavior: Implements operations such as jacketing and geometry cleanup.

### `DataprepGeometryFilters` / `DataprepGeometrySelectionTransforms`
- Role: Filter and selection helpers for geometry-specific pipeline steps.
- Key behavior: Define which geometry subsets to process and how selections are modified.

### `FJacketingProcess`
- Role: Utility struct/class implementing jacketing logic for simplification or occlusion removal workflows.

## 4. Typical usage patterns

- Enable alongside `DataprepEditor` when geometry cleanup steps are required in Dataprep pipelines.
- In the Dataprep Editor, add the provided geometry operations to a pipeline to filter or process meshes.
- Iterate in the editor to preview the effect of jacketing or other geometry operations on imported assets.

## 5. Version-specific notes (UE 5.7)

- Marked experimental and disabled by default; no additional UE 5.7-specific notes present.
