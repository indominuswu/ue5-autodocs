# Field Notification Trace Plugin Overview

## 1. What this plugin does

- Adds tracing support for `INotifyFieldValueChanged` objects, emitting trace events when field values change or when objects are tracked.
- Provides runtime tracing hooks and an editor-side analyzer/provider to visualize field notifications in trace tools (Gameplay Insights/Trace).
- Disabled by default; beta status.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers enable tracing macros (`UE_TRACE_FIELDNOTIFICATION_*`) and use the provided analyzer/provider to inspect field notifications in Gameplay Insights/Rewind Debugger.

## 3. Key Modules

- **FieldNotificationTrace** (Runtime, Default)  
  - Role: Emits trace events for field notification lifetimes and updates when tracing is enabled.  
  - Notable types: `UE::FieldNotification::FTrace`, macro wrappers (`UE_TRACE_FIELDNOTIFICATION_*`), `FFieldNotificationTraceModule`.

- **FieldNotificationTraceEditor** (Editor, Default)  
  - Role: Trace analyzer/provider and editor integration for viewing field notifications in trace/rewind tools.  
  - Notable types: `FFieldNotificationTraceEditorModule`, `FFieldNotificationTraceAnalyzer`, `FFieldNotificationTraceProvider`, `FFieldNotificationTraceServices`, `FFieldNotificationTrack`, `FFieldNotificationRewindDebugger`.

## 4. Important Types & APIs

### `UE::FieldNotification::FTrace` (runtime)

- Role: Static trace emitter.  
- Key APIs: `OutputObjectBegin`, `OutputObjectEnd`, `OutputUpdateField`, plus macros `UE_TRACE_FIELDNOTIFICATION_LIFETIME_BEGIN/END` and `UE_TRACE_FIELDNOTIFICATION_FIELD_VALUE_CHANGED`.
- Guarded by `UE_FIELDNOTIFICATION_TRACE_ENABLED` (only when tracing enabled, non-program, non-shipping).

### Editor trace components

- `FFieldNotificationTraceAnalyzer`: Processes trace events.  
- `FFieldNotificationTraceProvider`: Stores trace data for visualization.  
- `FFieldNotificationTraceServices`: Utilities to pull data into UI.  
- `FFieldNotificationTrack`: Track rendering for trace viewers.  
- `FFieldNotificationRewindDebugger`: Integration with rewind debugger UI.

## 5. Typical usage patterns

- Enable the plugin and tracing; instrumented field-notification objects emit events via the provided macros.  
- Use Gameplay Insights/Trace tools to analyze field notifications with the analyzer/provider and visualize tracks or rewind debugger data.

## 6. Version-specific notes (UE 5.7)

- Marked Beta and off by default. No explicit UE 5.7-only changes noted; overview reflects the 5.7 source.

