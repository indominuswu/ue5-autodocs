# UAF Pose Search Plugin Overview

## 1. What this plugin does

- Integrates Pose Search/motion matching features into UAF/AnimNext graphs.
- Provides traits, history collectors, and RigVM units to query pose databases and emulate results inside AnimNext.
- Disabled by default.

## 2. Key Modules

- **UAFPoseSearch** (Runtime)
  - Role: Runtime traits and helpers for Pose Search-driven motion matching in AnimNext graphs.
- **UAFPoseSearchUncookedOnly** (UncookedOnly)
  - Role: Authoring-time node templates for motion matching.

## 3. Important Types & APIs

### Traits and data

- `FMotionMatchingTrait` / `FMotionMatchingTraitData` implement motion-matching behavior in AnimNext.
- `FHistoryCollectorTrait` / `FHistoryCollectorTraitData` gather pose history used for matching.
- `FPoseSearchResultEmulatorTrait` simulates pose search outputs.

### Pose history interfaces

- `IPoseHistory`, `FPoseHistoryChooserParameter`, and `FPoseHistoryEvaluation` structures expose history data to choosers/search.

### RigVM utilities

- `FRigUnit_DebugDrawTrajectory`, `FRigUnit_GenerateCharacterMovementComponentTrajectory`, `FRigUnit_PoseSearchDatabaseGetTags`, and related units help debug and query pose search databases.

## 4. Typical usage patterns

- Add motion-matching and history collector traits to AnimNext graphs to drive animation selection from Pose Search databases.
- Use RigVM units to debug trajectories or query database tags when tuning search parameters.
- Employ uncooked node templates to scaffold motion-matching nodes during graph authoring.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
