# Motion Trajectory Plugin Overview

## 1. What this plugin does

- Generates character motion history and prediction data for motion matching and trajectory-driven animation.
- Provides a reusable component that samples `ACharacter` movement and builds trajectories.
- Includes Blueprint-ready structs and helper library for configuring sampling rates and predictions.
- Experimental and off by default.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Character teams add `UCharacterTrajectoryComponent`, configure `FTrajectorySamplingData`, and feed the output to motion-matching/pose-search systems.

## 3. Key Modules

- **MotionTrajectory** (Runtime) — trajectory sampling component, data structures, and utility library.

## 4. Important Types & APIs

- `UCharacterTrajectoryComponent` — actor component (Blueprint spawnable) that hooks `CharacterMovementComponent` updates, records trajectory history, and predicts future motion.
- `FTrajectorySamplingData` — configurable sampling settings (history/prediction lengths and sample rates).
- `FCharacterTrajectoryData` — stores sampled trajectory data and provides prediction helpers.
- `UMotionTrajectoryLibrary` — helper functions for working with trajectory types in Blueprints/C++.
- `FMotionTrajectorySettings` — settings struct referenced by the component and library.

## 5. Typical usage patterns

- Enable the plugin and add `UCharacterTrajectoryComponent` to a character; configure `FTrajectorySamplingData` to match motion-matching database needs.
- Use the component’s trajectory output with motion-matching or pose-search systems to drive animation selection.
- For custom movement components, extend or replace the provided component to feed trajectory data from bespoke movement modes.

## 6. Version-specific notes (UE 5.7)

- Marked experimental in 5.7; no additional version-specific behaviors noted.

