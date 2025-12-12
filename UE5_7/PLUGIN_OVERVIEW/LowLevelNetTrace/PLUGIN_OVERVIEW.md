# Low-level network trace Plugin Overview

## 1. What this plugin does

- Provides a lightweight module to sample system network throughput for profiling.
- Exposes a simple snapshot API (upload/download Mbps and timestamp) for tools or in-game diagnostics.
- Enabled by default in non-shipping builds when tracing is available.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers call `ILowLevelNetTraceModule::GetSnapshot` to retrieve upload/download Mbps samples for debugging/profiling.

## 3. Key Modules

- **LowLevelNetTrace** (Runtime)
  - Role: Defines the module interface and snapshot struct for querying network throughput.
  - Notable types: `ILowLevelNetTraceModule`, `FLowLevelNetTraceSnapshot`.

## 4. Important Types & APIs

### `FLowLevelNetTraceSnapshot`

- Role: Holds a single network measurement (`UploadMbps`, `DownloadMbps`, `TimeStamp`).

### `ILowLevelNetTraceModule`

- Role: Module interface exposed via `FModuleManager`.
- Key functions: `Get()`/`IsAvailable()` helpers and pure virtual `GetSnapshot(FLowLevelNetTraceSnapshot& OutSnapshot)` to fetch the latest measurement.
- Compile guard: `UE_LOW_LEVEL_NET_TRACE_ENABLED` defaults to enabled for non-shipping builds when UE_TRACE is on.

## 5. Typical usage patterns

- Check `ILowLevelNetTraceModule::IsAvailable()` and call `Get().GetSnapshot(...)` to retrieve the latest throughput sample.
- Use the snapshot data for on-screen debug displays or to feed custom profiling dashboards.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

