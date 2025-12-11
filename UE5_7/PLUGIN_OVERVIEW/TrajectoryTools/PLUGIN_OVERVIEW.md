# Trajectory Tools Plugin Overview

## 1. What this plugin does
- Experimental editor workflows for extracting and managing gameplay trajectories from recorded data.
- Provides export operations and UI for browsing trajectory data.
- Integrates with Gameplay Insights for data sourcing.

## 2. Key Modules
- **TrajectoryTools** (Editor)
  - Role: Trajectory export operations, UI, and debugger extensions.
  - Notable types: `TrajectoryExportOperation`, `TrajectoryLibrary`, Slate windows (`SExportTrajectoriesWindow`), and debugger hook `TrajectoryRewindDebuggerExtension`.

## 3. Important Types & APIs
### `TrajectoryExportOperation`
- Role: Performs extraction/export of trajectories from recordings or insights data.

### `TrajectoryLibrary`
- Role: Helper library for constructing or querying trajectory datasets.

### `SExportTrajectoriesWindow`
- Role: Editor window for selecting sources and launching exports.

### `TrajectoryRewindDebuggerExtension`
- Role: Extends rewind debugger to visualize or manage trajectory playback.

## 4. Typical usage patterns
- Enable the plugin (depends on GameplayInsights).
- Open the trajectory export window to pick source recordings and export trajectories.
- Use the rewind debugger extension to visualize trajectories in editor.
- Consume exported trajectories in gameplay tooling as needed.

## 5. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
