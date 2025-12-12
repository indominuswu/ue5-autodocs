# Input Debugging Plugin Overview

## 1. What this plugin does

- Adds runtime and editor utilities for visualizing and logging input devices, touch points, and hardware identifiers.
- Registers console commands and HUD overlays to inspect current input state.
- Editor module hooks into tooling to expose the same debug features in editor sessions.
- Disabled automatically for Shipping builds.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Provides console commands and HUD/touch visualizers (`FInputDeviceDebugTools`, `FTouchInputVisualizer`) that users enable to debug input devices in editor/runtime.

## 3. Key Modules

- **InputDebugging** (Runtime, Default, not in Shipping) — Core debug tooling, console commands, and Slate input processors.
- **InputDebuggingEditor** (Editor, Default) — Registers the runtime tooling for editor use and ties into editor startup.

## 4. Important Types & APIs

### `FInputDeviceDebugTools`

- Role: Console-driven debugger that logs connected devices, hardware identifiers, and renders debug HUD info.
- Key behaviors: registers console commands to list devices and draw per-device properties on the HUD.

### `FTouchInputVisualizer`

- Role: Slate input processor that captures touch/mouse events and renders their positions/pressure for debugging.
- Key behaviors: maintains live touch-point map and draws markers via `OnDebugDraw`.

## 5. Typical usage patterns

- Enable the plugin (default-on for non-Shipping). Use console commands registered by `FInputDeviceDebugTools` to list devices or toggle HUD overlays.
- In editor PIE/Simulate, the editor module ensures the debug overlays and touch visualizer are available; enable them via console or debug flags.
- Suitable for diagnosing platform-specific input mappings and hardware identifiers without custom instrumentation.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-only changes surfaced; behavior reflects the current source layout with shipping builds automatically excluding the features.

