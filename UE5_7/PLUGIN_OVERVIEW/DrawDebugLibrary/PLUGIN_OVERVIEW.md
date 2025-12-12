# Draw Debug Library Plugin Overview

## 1. What this plugin does
- Adds an extensive Blueprint function library for debug rendering, including lines, shapes, text, skeletons, and trajectories.
- Provides a unified `FDebugDrawer` wrapper so the same Blueprint nodes can target `UWorld`, `FPrimitiveDrawInterface`, AnimInstance proxies, or the Visual Logger.
- Exposes style structs (point, line, arrow, string, graph settings) so debug visuals can be parameterized.
- Intended for developer visualization; disabled by default and marked experimental.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Blueprint function library (`UDrawDebugLibrary`) gives users debug draw nodes and style structs for in-game/editor visualization.

## 3. Key Modules
- **DrawDebugLibrary** (Runtime)  
  - Role: Implements the debug drawing API and Blueprint nodes.

## 4. Important Types & APIs

### `UDrawDebugLibrary` (BlueprintFunctionLibrary)
- Role: Blueprint-callable entry point for all debug drawing operations.
- Key functions: Constructors for `FDebugDrawer` (world, PDI, anim instance, Visual Logger), drawing primitives (`DrawDebugPoints`, `DrawDebugLines`, `DrawDebugArrow`, `DrawDebugTransform`), complex helpers (poses, skeletons from `USkinnedMeshComponent`, trajectories), text/graph drawing, and Visual Logger variants.
- Styles: Most functions accept `FDrawDebugLineStyle`, `FDrawDebugPointStyle`, `FDrawDebugStringSettings`, or `FDrawDebugArrowSettings` for consistent look.

### `FDebugDrawer`
- Role: Lightweight wrapper that routes draw calls to a world, PDI, anim proxy, or Visual Logger.
- Creation helpers: `MakeDebugDrawer`, `MakeVisualLoggerDebugDrawer`, and merge helpers to combine multiple drawers.

### Style/Data structs
- `FDrawDebugPointStyle`, `FDrawDebugLineStyle`, `FDrawDebugArrowSettings`, `FDrawDebugStringSettings`, `FDrawDebugGraphAxesSettings` configure visuals; additional settings structs cover chairs, doors, skeletons, graphs, etc.

### Enums
- `EDrawDebugLogVerbosity` maps Visual Logger verbosity to Blueprint.
- `EDrawDebugLineType`, `EDrawDebugArrowHead` control line/arrow rendering variants.

## 5. Typical usage patterns
- Enable the plugin, then call nodes from `Draw Debug Library` in Blueprints to visualize gameplay data.
- Create a `FDebugDrawer` from a world or actor (`MakeDebugDrawer`) and pass it into draw nodes to render in the level viewport; use `MakeVisualLoggerDebugDrawer` to emit to the Visual Logger.
- Use style structs to reuse appearance presets across calls; use trajectory/skeleton helpers for animation debugging.
- Works in-editor and PIE for developer-only visualization; not intended for shipping builds.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

