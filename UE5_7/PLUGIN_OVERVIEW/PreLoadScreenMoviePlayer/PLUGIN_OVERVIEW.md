# Pre-Load Screen Movie Player Plugin Overview

## 1. What this plugin does

- Provides a default movie player implementation that runs during the Pre-Load screen phase.
- Integrates with the engine’s movie player pipeline to display loading videos before the main map loads.
- Supplies reusable base classes for screens and modules to customize movie playback during early startup.

## 2. Key Modules

- **PreLoadScreenMoviePlayer** (RuntimeNoCommandlet)  
  - Role: Implements the Pre-Load screen movie player module and base classes.
  - Notable types: `FPreLoadMoviePlayerModule`, `FPreLoadMoviePlayerModuleBase`, `FPreLoadMoviePlayerScreenBase`, `FMoviePlayerAttributes`.

## 3. Important Types & APIs

### `FPreLoadMoviePlayerModule` / `FPreLoadMoviePlayerModuleBase`

- Role: Module interface and base class wiring the movie player into the Pre-Load screen lifecycle.
- Key functions: Initialization/teardown hooks, registration of screen implementations.

### `FPreLoadMoviePlayerScreenBase`

- Role: Base class for custom screens shown during the Pre-Load phase.
- Key functions: `Tick`, `Initialize`, and hooks to drive playback/skip logic; uses `FMoviePlayerAttributes` to describe media.

### `FMoviePlayerAttributes`

- Role: Data structure describing media URLs, playback flags, skippable behavior, and loading screen properties.

## 4. Typical usage patterns

- Enable the plugin and configure a Pre-Load screen to use a movie-based implementation (e.g., via project settings or a custom module).
- Derive from `FPreLoadMoviePlayerScreenBase` to implement custom playback rules, then register it through the module during startup.
- Works in packaged builds to show a video before the main loading screen/map; no editor UI is provided.

## 5. Version-specific notes (UE 5.7)

- Disabled by default; intended for projects that need a Pre-Load movie flow in UE 5.7.
- No explicit UE 5.7-specific APIs or deprecations surfaced in the code reviewed.
