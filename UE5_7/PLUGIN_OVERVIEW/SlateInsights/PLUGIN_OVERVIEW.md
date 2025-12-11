# Slate Insights Plugin Overview

## 1. What this plugin does
- Pipes Slate tracing data into Unreal Insights so UI input, paint, and tick timings can be profiled.
- Adds custom timing tracks and widgets (frame schematic, update steps) to visualize Slate behavior per frame.
- Supplies a trace analyzer/provider pair so captured events are stored and queried inside Insights.
- Targeted for the `UnrealInsights` program; not intended for packaged games.

## 2. Key Modules
- **SlateInsights** (EditorAndProgram)
  - Role: Integrates Slate trace events with Unreal Insights, registers analyzers/providers, and extends the Insights UI with Slate-specific tracks and views.
  - Notable types: `FSlateAnalyzer`, `FSlateProvider`, `FSlateTraceModule`, `FSlateTimingViewSession`, `FSlateFrameGraphTrack`, `SSlateFrameSchematicView`.

## 3. Important Types & APIs
- `FSlateAnalyzer`
  - Role: Trace analyzer that consumes Slate trace channels and forwards data into the provider for storage.
  - Notes: Handles registration with the Insights analysis service.
- `FSlateProvider`
  - Role: Data store queried by Insights UI elements to retrieve per-frame widget/update information.
  - Notes: Owns event buffers used by the timing tracks and schematic view.
- `FSlateTimingViewSession`
  - Role: Adds Slate timing tracks to the Insights timing view.
  - Key views: widget update steps timing, frame graph visualization.
- `FSlateTraceModule`
  - Role: Module entry point that wires the analyzer/provider into Insights during startup.
- `SSlateFrameSchematicView`
  - Role: Custom Insights widget that visualizes widget hierarchy timing for a frame.

## 4. Typical usage patterns
- Enable the Slate Insights plugin when running `UnrealInsights`; capture or load traces that include Slate channels.
- In Insights, open the timing view to see Slate-specific tracks (frame graph, widget update steps) provided by the plugin.
- Use the schematic view to identify expensive widgets or problematic update sequences.
- No runtime/editor Blueprint APIs; usage is confined to the Insights tooling environment.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
