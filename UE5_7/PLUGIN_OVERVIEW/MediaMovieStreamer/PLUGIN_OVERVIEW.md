# Media Movie Streamer Plugin Overview

## 1. What this plugin does

- Implements an `IMovieStreamer` that uses Media Framework to play startup/loading movies.
- Supports external control of the media player, sound component, and texture while a map loads.
- Targets movie playback during level loads or application startup.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developers select the Media-based `FMediaMovieStreamer`, provide media player/sound/texture assets, and optionally control playback externally for startup/loading movies.

## 3. Key Modules

- **MediaMovieStreamer** (Runtime)
  - Role: Provides the Media-based movie streamer implementation and module interface.
  - Notable types: `FMediaMovieStreamer`, `IMediaMovieStreamerModule` (module header in `MediaMovieStreamerModule.h`).

## 4. Important Types & APIs

### `FMediaMovieStreamer`

- Role: `IMovieStreamer` implementation that wraps `UMediaPlayer`, `UMediaSoundComponent`, and media textures to present movies during loads.
- Key functions: `SetIsMediaControlledExternally`, setters for media assets, and lifecycle overrides from `IMovieStreamer` to start/stop/advance playback.
- Behavior: Can relinquish cleanup/control when `SetIsMediaControlledExternally(true)` is used, allowing callers to manage media assets manually.

## 5. Typical usage patterns

- Enable the plugin and configure the Movie Player to use the Media movie streamer.
- Provide media source/player/sound component/texture to the streamer; optionally set external control if another system manages playback.
- Use for startup movies or loading screens where Media Framework playback is required instead of file-based movie formats.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

