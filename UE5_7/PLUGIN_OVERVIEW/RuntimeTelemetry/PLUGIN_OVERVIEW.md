# Editor Telemetry Plugin Overview

## 1. What this plugin does

- Emits common telemetry events from the editor for instrumentation such as IoStore on-demand usage and memory LLM tracking.
- Provides a simple runtime/program module that can be invoked from code to start/end telemetry sessions and log key events.

## 2. Editor/Runtime surfaces

- User-facing: No - Internal telemetry helper for editor instrumentation; no editor UI or gameplay-facing APIs beyond C++ event hooks.

## 3. Key Modules

- **RuntimeTelemetry** (RuntimeAndProgram, PostConfigInit)  
  - Role: Owns the telemetry provider, session lifecycle, and helper functions for emitting common editor telemetry events.

## 4. Important Types & APIs

### `FRuntimeTelemetry`

- Role: Singleton-style helper that starts/stops telemetry sessions and exposes canned event helpers.
- Key functions: `StartSession()`, `EndSession()`, `RecordEvent_IoStoreOnDemand(Context, Attributes)`, `RecordEvent_MemoryLLM(Context, Attributes)`.

### `FRuntimeTelemetryModule`

- Role: Module wrapper that brings the telemetry system online during startup and tears it down on shutdown.

## 5. Typical usage patterns

- Enable the plugin (on by default) to have editor telemetry available.
- From editor or program code, call `FRuntimeTelemetry::Get().StartSession()` / `EndSession()` to bracket a telemetry window.
- Use the helper event methods to record IoStore and memory LLM events with contextual attributes.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

