# Timed Data Monitor Plugin Overview

## 1. What this plugin does

- Monitors time-synchronized input sources (e.g., LiveLink, media, or custom timed data providers).
- Provides an engine subsystem that evaluates connection state, latency, and buffer ranges, plus editor panels for visualization.
- Intended as the replacement for the deprecated TimecodeSynchronizer workflow.

## 2. Key Modules

- **TimedDataMonitor** (UncookedOnly)
  - Role: Registers the engine subsystem and runtime evaluation helpers for timed data channels.
- **TimedDataMonitorEditor** (Editor)
  - Role: Slate panels, buffer visualizers, numeric entry widgets, and editor settings/style for monitoring.

## 3. Important Types & APIs

### `UTimedDataMonitorSubsystem`

- Role: Engine subsystem tracking timed inputs/channels, connection events, evaluation state, and calibration.
- Key data: `ETimedDataMonitorInputEnabled`, `ETimedDataMonitorEvaluationState`, `FTimedDataMonitorChannelConnectionStateEvent`; integrates with stage messaging for status updates.

### `FTimedDataMonitorCalibration` / `FTimedDataMonitorTypes`

- Role: Structures describing tolerances, sampling windows, and evaluation parameters used by the subsystem.

### Editor widgets and settings

- Role: `STimedDataMonitorPanel`, `STimedDataMonitorBufferVisualizer`, `STimedDataGenlock`, `STimingDiagramWidget`, and `UTimedDataMonitorEditorSettings` expose UI and preferences for monitoring.

## 4. Typical usage patterns

- Enable the plugin and open the Timed Data Monitor panel to inspect incoming time-synchronized sources and their buffer health.
- Use the subsystem to emit channel connection events and evaluation state for tooling or automation that depends on synchronized inputs.
- Configure editor settings to adjust visualization and thresholds when comparing multiple inputs.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
