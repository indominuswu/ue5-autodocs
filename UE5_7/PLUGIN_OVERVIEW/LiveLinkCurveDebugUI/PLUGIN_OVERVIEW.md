# Live Link Curve Debug UI Plugin Overview

## 1. What this plugin does
- Adds runtime UI helpers to visualize and debug Live Link curve data.
- Provides Blueprint accessors to read curve values and toggle debug overlays for active Live Link subjects.
- Intended for validating streamed animation data while iterating in PIE or game builds.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Blueprint library/settings (`ULiveLinkDebuggerBlueprintLibrary`, `ULiveLinkDebuggerSettings`) let users visualize Live Link curves at runtime/PIE.

## 3. Key Modules
- **LiveLinkCurveDebugUI** (Runtime)  
  - Runtime-only utilities for inspecting Live Link curves.  
  - Notable types: `ULiveLinkDebuggerBlueprintLibrary`, `ULiveLinkDebuggerSettings`.

## 4. Important Types & APIs

### `ULiveLinkDebuggerBlueprintLibrary`
- Role: Blueprint function library to query/debug Live Link curve data at runtime.
- Typical APIs: enable/disable debugging, fetch per-subject curve samples for display (see BlueprintCallable functions in the class).

### `ULiveLinkDebuggerSettings`
- Role: Configurable settings for what data to display and how the debug overlay behaves.

## 5. Typical usage patterns
- Enable alongside the core Live Link plugin.
- In PIE or runtime, call `ULiveLinkDebuggerBlueprintLibrary` nodes to turn on curve debug visualization for a specific Live Link subject.
- Adjust defaults via `ULiveLinkDebuggerSettings` (e.g., which curves to show, thresholds/filters).

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

