# AutomatedPerfTesting Plugin Overview

## 1. What this plugin does

- Provides Gauntlet test controllers and utilities for automated performance testing.
- Supplies developer settings for multiple perf test variants (material, profile-go, replay, sequence, static camera).
- Includes engine subsystems that coordinate perf test execution and data collection.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Exposes project settings and Gauntlet-facing subsystems to configure and run automated perf test variants.

## 3. Key Modules

- **AutomatedPerfTesting** (Runtime)  
  - Role: Perf test controllers, project settings, and runtime subsystems used during automated runs.

## 4. Important Types & APIs

### Developer settings

- `UAutomatedPerfTestProjectSettings`, `UAutomatedMaterialPerfTestProjectSettings`, `UAutomatedProfileGoTestProjectSettings`, `UAutomatedReplayPerfTestProjectSettings`, `UAutomatedSequencePerfTestProjectSettings`, `UAutomatedStaticCameraPerfTestProjectSettings`.
- Role: Configure maps, camera behaviors, profile targets, and capture options for each perf test flavor.

### `UAutomatedPerfTestSubsystem` (UEngineSubsystem)

- Role: Coordinates execution of automated perf tests within the engine context.

### `UProfileGoSubsystem` (UTickableWorldSubsystem)

- Role: Drives “ProfileGo” runs from Gauntlet/automation, ticking and updating test progress.

## 5. Typical usage patterns

- Enable the plugin for projects that run Gauntlet-based perf tests.
- Set up desired test settings in project configs (e.g., default maps, camera cuts, replay or sequence assets).
- Trigger perf tests via Gauntlet/automation; the subsystems manage runtime execution and data capture.
- Use ProfileGo helpers to run specific profiling passes with command-line control.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
