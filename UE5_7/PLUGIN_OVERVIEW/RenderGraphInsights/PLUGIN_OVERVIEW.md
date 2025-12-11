# RDG Insights Plugin Overview

## 1. What this plugin does
- Integrates Render Dependency Graph (RDG) tracing with Unreal Insights for debugging render passes.
- Provides an Insights timing view extender and tracks to visualize RDG events.

## 2. Key Modules
- **RenderGraphInsights** (EditorAndProgram)  
  - Exposes RDG trace provider, analyzer, timing view extensions, and track drawing helpers to Insights.

## 3. Important Types & APIs
- `FRenderGraphTraceModule`, `FRenderGraphProvider`, `FRenderGraphAnalyzer`: capture and parse RDG trace data.
- `FRenderGraphTimingViewSession` / `FRenderGraphTimingViewExtender`: add RDG lanes/visuals inside Insights timing view.
- `FRenderGraphTrack` and `FRenderGraphTrackDrawHelper`: render RDG nodes, barriers, and timings.

## 4. Typical usage patterns
- Enable the plugin, capture traces with RDG tracing enabled, then open the session in Unreal Insights.
- Use the RDG tracks to inspect pass order, dependencies, and timing; timing view extender adds RDG-specific visualization alongside other GPU/CPU tracks.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

