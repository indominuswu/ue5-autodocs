# XGE Controller Plugin Overview

## 1. What this plugin does
- Adds distributed shader compilation support via IncrediBuild/XGE on Win64.
- Implements an `IDistributedBuildController` that marshals compile tasks to an external XGE controller process.
- Manages task queues, named pipes, and controller lifecycle for shader compiler workers.
- Enabled by default on Windows editor/uncooked targets; runs at the earliest loading phase.

## 2. Key Modules
- **XGEController** (UncookedOnly, Win64): The sole module; wires into the distributed build interface used by the shader compiler.

## 3. Important Types & APIs
- `FXGEControllerModule` (`IDistributedBuildController`): Module singleton with `Get`; handles startup/shutdown, controller initialization, task enqueueing, and worker management.
- Task management: maintains pending/dispatched task queues (`TQueue`, `TMap`), generates unique file/task IDs, and communicates with XGE via named pipes and background threads.
- Provides `EnqueueTask`, `CreateUniqueFilePath`, and `SupportsLocalWorkers` overrides used by the engine’s shader compiler distribution path.

## 4. Typical usage patterns
- Enable the plugin on Win64 to allow shader compile distribution; the build system will call into `FXGEControllerModule` automatically.
- The module spins up the XGE controller process, monitors events through read/write threads, and reports completion back to the engine.
- No direct gameplay/runtime usage; intended for build acceleration.

## 5. Version-specific notes (UE 5.7)
- Windows-only and non-shipping (UncookedOnly). No additional UE 5.7-specific changes noted.
