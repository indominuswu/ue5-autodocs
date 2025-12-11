# Mass Insights Plugin Overview

## 1. What this plugin does

- Adds Unreal Insights analysis support for Mass traces, including custom timing tracks and analysis tabs.
- Provides analysis-side data models plus UI extensions to visualize Mass execution within Unreal Insights sessions.
- Targets both editor and the UnrealInsights program.

## 2. Key Modules

- **MassInsightsAnalysis** (EditorAndProgram)
  - Role: Parses Mass trace data and exposes analysis models for Insights.
  - Notable types: `FMassInsights` model definitions (time-ranged events, lanes).
- **MassInsightsUI** (EditorAndProgram)
  - Role: Integrates with the Insights UI, registers tabs/layout extensions, and draws timing tracks.
  - Notable types: `FMassInsightsUIModule`, `FMassInsightsTimingTrack`, `SMassInsightsAnalysisTab`.

## 3. Important Types & APIs

### `FMassInsights`

- Role: Core data structure representing Mass analysis ranges (begin/end times, text, IDs, depth) used to populate timing tracks.

### `FMassInsightsUIModule`

- Role: Insights UI module that registers the Mass analysis tab and layout extensions.
- Key functions: `StartupModule`, `ShutdownModule`, `GetAnalysisTab()` to retrieve/create the tab.

### `FMassInsightsTimingTrack`

- Role: Custom timing track renderer for Mass data within Insights, consuming `FMassInsights` model data.

## 4. Typical usage patterns

- Enable the plugin when capturing or analyzing Mass traces.
- Open Unreal Insights; the Mass Insights UI module adds a Mass Analysis tab and timing track visualizations for Mass events.
- Use the track to correlate Mass simulation phases/processors with other engine traces during performance investigation.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
