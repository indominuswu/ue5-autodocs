# Editor Telemetry Plugin Overview

## 1. What this plugin does
- Emits common telemetry events from the editor to evaluate workflow efficiency.
- Provides preconfigured analytics spans for boot, PIE, cooking, asset registry scanning, loading, and hitch detection.
- Enabled by default in editor builds to centralize telemetry routing.

## 2. Editor/Runtime surfaces

- User-facing: No - Internal editor telemetry helper; records analytics events but exposes no end-user workflows or gameplay APIs.

## 3. Key Modules
- **EditorTelemetry** (Editor)  
  - Role: Owns telemetry routing and exposes helpers for recording standard events.

## 4. Important Types & APIs

### `FEditorTelemetry`
- Role: Singleton-style helper that starts/ends sessions and records standardized analytics events.
- Key functions: `StartSession`, `EndSession`, `RecordEvent_Cooking`, `RecordEvent_Loading`, `RecordEvent_CoreSystems`, `RecordEvent_DDCResource`, `RecordEvent_DDCSummary`, `RecordEvent_Zen`, `RecordEvent_VirtualAssets`, `RecordEvent_MemoryLLM`, and `RegisterCollectionWorkflowDelegates`.
- Maintains analytics spans (editor, PIE, cooking, hitching, asset registry) and heartbeat/hitch sampler timers.

## 5. Typical usage patterns
- Enabled plugin automatically sets up telemetry. Call `FEditorTelemetry::Get()` from editor modules to emit standard events with contextual attributes.
- Use `RegisterCollectionWorkflowDelegates` to hook workflow events into existing systems; spans track durations for boot, map load, PIE, etc.
- Intended for internal telemetry; requires analytics provider configuration.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific changes noted; functionality reflects current source.

