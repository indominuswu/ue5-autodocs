# MovieSceneTextTrack Plugin Overview

## 1. What this plugin does
- Provides legacy Sequencer text tracks and sections (deprecated; text support moved to core Movie Scene Tracks).
- Runtime evaluation and editor tooling for text sections remain available for older content.

## 2. Key Modules
- **MovieSceneTextTrack** (Runtime)
  - Role: Runtime text track/section types and evaluation systems.
  - Notable types: `UMovieSceneTextTrack`, `UMovieSceneTextSection`, `UMovieSceneTextChannel`, `UTextChannelEvaluatorSystem`, `UMovieSceneTextPropertySystem`, `FTextComponentTypes`.
- **MovieSceneTextTrackEditor** (Editor)
  - Role: Editor support for authoring text tracks.

## 3. Important Types & APIs

### `UMovieSceneTextTrack` / `UMovieSceneTextSection`
- Role: Sequencer track and section for displaying text over time.
- Key properties: text channel data (`UMovieSceneTextChannel`) controlling displayed strings and timing.

### `UTextChannelEvaluatorSystem` and `UMovieSceneTextPropertySystem`
- Role: Runtime systems that evaluate text channels and apply them to bound properties/components during playback.

## 4. Typical usage patterns
- Intended for existing projects that rely on the deprecated text track; new projects should use built-in Movie Scene Tracks text support.
- Add/edit text sections in Sequencer; runtime systems evaluate channels on playback.

## 5. Version-specific notes (UE 5.7)
- Plugin is explicitly marked deprecated; no additional UE 5.7-specific notes beyond the deprecation notice.
