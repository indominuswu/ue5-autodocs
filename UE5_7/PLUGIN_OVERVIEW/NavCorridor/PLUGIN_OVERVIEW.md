# NavCorridor Plugin Overview

## 1. What this plugin does
- Experimental navigation corridor generation for pathfinding.
- Provides parameters and debug/testing component for visualizing corridor results.
- Implements corridor portal/sector computation to keep agents away from obstacles.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Exposes `UNavCorridorTestingComponent` and `FNavCorridorParams` that developers use to visualize/tune corridor generation in editor/runtime navigation experiments.

## 3. Key Modules
- **NavCorridor** (Runtime)
  - Role: Runtime corridor builder and testing component.
  - Notable types: `FNavCorridorParams`, `FNavCorridorPortal`, `FNavCorridor`, `UNavCorridorTestingComponent`.

## 4. Important Types & APIs

### `FNavCorridorParams`
- Role: Parameter struct controlling corridor width, offsets, simplification thresholds, and portal simplification toggles.
- Key properties: `Width`, `PathOffsetFromBoundaries`, `ObstacleTaperAngle`, `SmallSectorThreshold`, `LargeSectorThreshold`, `SimplifyEdgeThreshold`, booleans for flip/convex/concave simplification.
- Helpers: `SetFromWidth`, `ToString`.

### `UNavCorridorTestingComponent`
- Role: Testing/visualization component for generating and drawing corridors in the editor or runtime.

## 5. Typical usage patterns
- Enable the plugin and attach `NavCorridorTestingComponent` to an actor to visualize generated corridors along navigation paths.
- Adjust `FNavCorridorParams` (width, simplification options) to see how corridors adapt to navigation obstacles.
- Integrate corridor generation into custom navigation code to guide agents with corridor-based avoidance.

## 6. Version-specific notes (UE 5.7)
- Plugin is marked experimental; no additional UE 5.7-specific notes found.

