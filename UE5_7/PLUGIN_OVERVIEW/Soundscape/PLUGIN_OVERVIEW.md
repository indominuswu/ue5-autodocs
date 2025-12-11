# Soundscape Plugin Overview

## 1. What this plugin does
- Implements a dynamic ambient sound system for layering environmental audio.
- Manages collections of palettes and color points to spawn and mix ambience procedurally.
- Provides editor tools for authoring palettes and tuning runtime behavior.

## 2. Key Modules
- **Soundscape** (Runtime)
  - Role: Runtime system handling palette/color point collections, streaming, and GameInstance-level management.
  - Notable types: `USoundscapeSubsystem`, `USoundscapePalette`, `USoundscapePaletteCollection`, `USoundscapeColorPoint`, `USoundscapeSettings`, `USoundscapeColorPointHashMap`.
- **SoundscapeEditor** (Editor)
  - Role: Editor integration for authoring and visualizing soundscape assets.

## 3. Important Types & APIs
- `USoundscapeSubsystem` (UGameInstanceSubsystem)
  - Role: Entry point for loading palettes, querying color points, and managing active soundscapes.
  - Key data: `FSoundscapePaletteCollection`, `FSoundscapeColorPointCollection`, streaming handles for palette assets.
- `USoundscapePalette` / `USoundscapePaletteCollection`
  - Role: Assets grouping ambient elements that can be activated at runtime.
- `USoundscapeColorPoint` and related hash-map classes
  - Role: Spatial distribution data used to spawn ambience based on location and density.
- `USoundscapeSettings` (UDeveloperSettings)
  - Role: Project-level tuning for soundscape behavior and debug options.

## 4. Typical usage patterns
- Enable the plugin, create soundscape palettes and color point assets, and assign them to collections.
- At runtime, obtain `USoundscapeSubsystem` to load/activate palette collections and manage active ambient layers.
- Use editor tooling to visualize color points and adjust palette parameters; rely on settings for global tuning.
- Combine with other audio systems (spatialization, reverb) for immersive ambience.

## 5. Version-specific notes (UE 5.7)
- Marked Beta in the `.uplugin`; no explicit UE 5.7-specific notes found.
