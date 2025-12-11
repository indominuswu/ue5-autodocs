# Insights Data Source Filters Plugin Overview

## 1. What this plugin does
- Adds filtering for trace data sources used by Unreal Insights.
- Provides runtime filter definitions/collections and editor UI to build, organize, and apply them.
- Integrates with GameplayInsights to prune trace data by class, world, or custom criteria before analysis.

## 2. Key Modules
- **SourceFilteringCore** (Runtime)  
  - Role: Core interfaces and helpers for data source filtering.  
  - Notable types: `IDataSourceFilterInterface`, `IDataSourceFilterSetInterface`, `FTraceSourceFilteringSettings`.
- **SourceFilteringTrace** (Runtime)  
  - Role: Implements trace-time filtering, filter sets, async tasks, and managers.  
  - Notable types: `FSourceFilter`, `FSourceFilterSet`, `FSourceFilterManager`, `FSourceFilterTrace`, `UTraceSourceFilteringSettings`, `UTraceSourceFilteringProjectSettings`.
- **SourceFilteringEditor** (Editor)  
  - Role: Editor UI, drag/drop, and services for building filter trees and editing presets.  
  - Notable types: `FSourceFilteringEditorModule`, `FEditorSessionSourceFilterService`, widgets such as `STraceSourceFilteringWidget`, `SClassTraceFilteringWidget`.

## 3. Important Types & APIs
### `UTraceSourceFilteringSettings` / `UTraceSourceFilteringProjectSettings`
- Role: Developer settings objects controlling filter assets, presets, and project-wide defaults.
- Key properties: enabled filters, default filter sets, save locations for presets.

### `FSourceFilter` and `FSourceFilterSet`
- Role: Runtime filter representations applied to trace events; sets aggregate multiple filters.
- Key behaviors: evaluate actor/world/class inclusion/exclusion, cache results (`FResultCache`), and manage async evaluation.

### `FSourceFilterManager`
- Role: Manages active filters in a session and coordinates filter setup with tracing backends.

## 4. Typical usage patterns
- Enable the plugin and open the Source Filtering UI to compose filters (by class, world, or custom logic) using provided widgets.
- Save filter sets/presets via the editor module; settings objects track defaults for projects and sessions.
- When tracing gameplay, the trace module applies active filters to reduce data volume before it reaches Insights or other consumers.

## 5. Version-specific notes (UE 5.7)
- Shipping builds are excluded per module configuration; plugin targets development/editor tracing workflows.
- No explicit UE 5.7-specific notes found; behavior matches the current source in this branch.
