# LevelSnapshots Plugin Overview

## 1. What this plugin does
- Captures and restores world state via Level Snapshots, with support for filtering properties and subsystem events.
- Provides Blueprint libraries and editor helpers to take/apply snapshots, compare properties, and integrate with filters (including foliage and nDisplay support modules).
- Exposes editor settings and factories for creating snapshot filters.

## 2. Key Modules
- **LevelSnapshots** (UncookedOnly)  
  - Role: Core snapshot capture/apply logic and Blueprint API.
  - Notable types: `ULevelSnapshotsEngineSubsystem`, `ULevelSnapshotsFunctionLibrary`, `ULevelSnapshot`.
- **LevelSnapshotFilters** (UncookedOnly)  
  - Role: Filter infrastructure and factories for snapshot filtering.
  - Notable types: `FilterBlueprintFunctionLibrary`, `LevelSnapshotFilterFactory`.
- **LevelSnapshotsEditor** (UncookedOnly)  
  - Role: Editor UI/integration and settings for snapshot workflows.
  - Notable types: `LevelSnapshotsEditorSettings`, `LevelSnapshotsEditorFunctionLibrary`, `AssetTypeActions_LevelSnapshot`, `LevelSnapshotEditorFactory`.
- **FoliageSupport**, **nDisplaySupport** (UncookedOnly)  
  - Role: Optional adapters extending snapshot support to foliage and nDisplay data.

## 3. Important Types & APIs

### `ULevelSnapshotsEngineSubsystem`
- Role: Engine subsystem exposing snapshot lifecycle events to Blueprints.
- Events: `OnPreTakeSnapshot`, `OnPostTakeSnapshot`, `OnPreApplySnapshot`, `OnPostApplySnapshot` carrying snapshot references.

### `ULevelSnapshotsFunctionLibrary`
- Role: Blueprint library for core snapshot actions.
- Key functions: `TakeLevelSnapshot`, `ApplySnapshotToWorld`, helper traversal functions for custom snapshot subobjects.

### Settings and filters
- `LevelSnapshotsSettings`/`LevelSnapshotsEditorSettings` control defaults such as compression and editor behavior.
- `FilterBlueprintFunctionLibrary` and filter factories enable creating custom snapshot filters to include/exclude properties or actors.

## 4. Typical usage patterns
- Runtime/editor scripting: Call `TakeLevelSnapshot` to capture the current world into a `ULevelSnapshot`, then `ApplySnapshotToWorld` with an optional filter to restore state selectively.
- Editor: Use the snapshot UI (provided by the editor module) to browse, compare, and apply snapshots; create filters via `LevelSnapshotFilterFactory`.
- Event hooks: Bind to `ULevelSnapshotsEngineSubsystem` events to react before/after snapshot capture or application (e.g., to pause simulation or log changes).

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; overview reflects the current implementation shipping with UE 5.7.

