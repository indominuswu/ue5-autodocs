# IoStore Insights Plugin Overview

## 1. What this plugin does

- Adds Unreal Insights integration for tracing and visualizing IoStore (I/O store) activity.
- Provides analyzers, data providers, and Slate widgets to inspect IoStore requests, timing, and bandwidth.
- Targets the `UnrealInsights` program; not used in packaged games.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Insights users enable this to analyze IoStore traces via the IoStore analysis tab and associated widgets/providers.

## 3. Key Modules

- **IoStoreInsights** (EditorAndProgram, Default; program allow list: UnrealInsights) — Registers analyzers, providers, and UI tabs for IoStore data in Insights.

## 4. Important Types & APIs

### Analysis and providers

- `FIoStoreInsightsAnalyzer` — Trace analyzer that processes IoStore trace events and feeds the model.
- `IIoStoreInsightsProvider` / `FIoStoreInsightsProvider` — Data interface/model storing parsed IoStore events and request metadata.

### UI & view models

- Slate widgets such as `SActivityTableTreeView`, `SIoStoreAnalysisTab`, and supporting view models (`FIoStoreActivityTable`, `FIoStoreActivityNode`, timing track/extender classes) expose IoStore timelines and tables inside Insights.

## 5. Typical usage patterns

- Run UnrealInsights with this plugin enabled; capture or load a trace containing IoStore events.
- Use the IoStore analysis tab to filter read events, inspect request timelines, and analyze histogram data provided by the plugin’s widgets.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; functionality is scoped to the UnrealInsights program module.

