# World Metrics Plugin Overview

## 1. What this plugin does
- Provides an experimental profiling framework for world-scoped metrics and extensions.
- Exposes a world subsystem that owns metric instances, extensions, and update loops.
- Includes sample CSV/actor-count metrics and test helpers for exercising the system.
- Enabled by default for supported programs (e.g., SpatialMetricsProfiler) but meant for profiling workflows.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Profiling framework with `UWorldMetricsSubsystem`, extensions, and metric interfaces for teams to implement/customize world metrics (CSV samples provided).

## 3. Key Modules
- **WorldMetricsCore** (RuntimeAndProgram): Core runtime subsystem, extension model, and metric interfaces.
- **CsvMetrics** (RuntimeAndProgram): Example metric implementations that write CSV output (e.g., actor count).
- **WorldMetricsTest** (RuntimeAndProgram): Test helpers and mock extensions for validation (not in Shipping).

## 4. Important Types & APIs
- `UWorldMetricsSubsystem` (WorldSubsystem): Entry point; `Get`/`CanHaveWorldMetrics`, acquires/releases `UWorldMetricsExtension` instances, drives metric updates.
- `UWorldMetricsExtension`: Base UObject living within the subsystem; use `AcquireExtension`/`ReleaseExtension` to manage lifetime and dependencies.
- `UWorldMetricInterface`: Base class for concrete metrics; implements `Update`, `Initialize`, `Deinitialize`, and reports memory usage via `GetAllocatedSize`.
- `UWorldMetricsActorTracker`: Extension that tracks actors entering/leaving the world and notifies `IWorldMetricsActorTrackerSubscriber` implementers.
- `IWorldMetricsActorTrackerSubscriber`: Interface for metrics/extensions that want actor add/remove notifications.
- `UCsvActorCountMetric`: Sample metric counting tracked actors and writing CSV output; implements `UWorldMetricInterface` and subscribes to the actor tracker.

## 5. Typical usage patterns
- Call `UWorldMetricsSubsystem::Get(World)` to access the subsystem; verify availability with `CanHaveWorldMetrics`.
- Acquire extensions or metrics via `AcquireExtension` and keep the returned pointer while active; call `ReleaseExtension` when done.
- Implement custom metrics by deriving from `UWorldMetricInterface`, performing work in `Update`, and optionally subscribing to `UWorldMetricsActorTracker` for actor events.
- Use CsvMetrics as reference implementations for capturing data to disk; register additional extensions/metrics in code.
- Tests under `WorldMetricsTest` provide mock extensions and utilities for validating lifecycle and dependency behavior.

## 6. Version-specific notes (UE 5.7)
- Plugin is marked experimental in this tree; no other UE 5.7-specific notes observed.

