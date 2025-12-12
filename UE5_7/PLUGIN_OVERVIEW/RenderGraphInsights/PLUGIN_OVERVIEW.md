# RDG Insights Plugin Overview

## 1. What this plugin does
- Integrates Render Dependency Graph (RDG) tracing with Unreal Insights for debugging render passes.
- Provides an Insights timing view extender and tracks to visualize RDG events.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Unreal Insights extension adding RDG providers/tracks so developers can visualize render graph passes in trace captures.

## 3. Key Modules
- **RenderGraphInsights** (EditorAndProgram)  
  - Exposes RDG trace provider, analyzer, timing view extensions, and track drawing helpers to Insights.

## 4. Important Types & APIs
- `FRenderGraphTraceModule`, `FRenderGraphProvider`, `FRenderGraphAnalyzer`: capture and parse RDG trace data.
- `FRenderGraphTimingViewSession` / `FRenderGraphTimingViewExtender`: add RDG lanes/visuals inside Insights timing view.
- `FRenderGraphTrack` and `FRenderGraphTrackDrawHelper`: render RDG nodes, barriers, and timings.

## 5. Typical usage patterns
- Enable the plugin, capture traces with RDG tracing enabled, then open the session in Unreal Insights.
- Use the RDG tracks to inspect pass order, dependencies, and timing; timing view extender adds RDG-specific visualization alongside other GPU/CPU tracks.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

