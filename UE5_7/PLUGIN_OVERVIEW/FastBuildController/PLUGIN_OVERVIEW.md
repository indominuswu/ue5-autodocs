# FastBuild Controller Plugin Overview

## 1. What this plugin does
- Adds support for distributing shader compilation tasks through FastBuild.
- Hooks into the build pipeline early to generate and submit FastBuild scripts for pending shader batches.
- Monitors remote build execution and collects results back into the engine pipeline.

## 2. Key Modules
- **FastBuildController** (UncookedOnly)
  - Role: Integrates FastBuild with the shader compile controller, manages job submission and monitoring.
  - Notable types: `FFastBuildControllerModule`, `FFastBuildJobProcessor`, `FFastBuildUtilities`.

## 3. Important Types & APIs

### `FFastBuildControllerModule`
- Role: Module entry that owns the job processor and coordinates shader batch distribution.
- Responsibilities: Startup/shutdown hooks, queuing shader compile tasks, feeding them to FastBuild.

### `FFastBuildJobProcessor`
- Role: `FRunnable` worker that writes FastBuild scripts, launches the FastBuild process, and polls results.
- Key behaviors: `StartThread()` to kick off processing, `Run()` main loop, `Stop()` for early exit, monitors process handles and output pipes.

### `FFastBuildUtilities`
- Role: Helper functions for interacting with the FastBuild environment (script generation, process helpers).

## 4. Typical usage patterns
- Enable the plugin on Win64/Mac/Linux development machines and configure FastBuild tooling paths in project build settings.
- During large shader builds, the controller generates FastBuild scripts from queued compile jobs and dispatches them to workers.
- Monitor build progress via engine logs; the controller re-integrates compiled shader results when workers finish.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-only changes surfaced; functionality is tied to the current 5.7 shader compile pipeline.
