# Media Compositing Plugin Overview

## 1. What this plugin does

- Adds Sequencer tracks and supporting data structures for playing and compositing media (video/audio) in cinematic timelines.
- Provides media sections/tracks for Media Players and media components, including audio integration.
- Supplies editor-side tooling for Sequencer to author and preview media-driven shots.

## 2. Key Modules

- **MediaCompositing** (Runtime)
  - Role: Defines Sequencer track/section types for media playback and evaluation templates.
  - Notable types: `UMovieSceneMediaTrack`, `UMovieSceneMediaSection`, `UMovieSceneMediaPlayerPropertyTrack`, `UMovieSceneMediaPlayerPropertySection`, `FMovieSceneMediaData`.
- **MediaCompositingEditor** (Editor)
  - Role: Sequencer/editor integration and UI for the media tracks.

## 3. Important Types & APIs

### `UMovieSceneMediaTrack` / `UMovieSceneMediaSection`

- Role: Sequencer track and sections that drive media playback (video/audio) during timeline evaluation.
- Key properties: Media source/texture/sound component references, and evaluation settings stored in `FMovieSceneMediaData`.

### `UMovieSceneMediaPlayerPropertyTrack` / `UMovieSceneMediaPlayerPropertySection`

- Role: Tracks targeting `UMediaPlayer` properties directly on bound objects.
- Behavior: Lets Sequencer control media players via property bindings rather than dedicated components.

### `FMovieSceneMediaData`

- Role: Data struct describing how a media section should play (looping, start frame, media source, sound component, texture).

## 4. Typical usage patterns

- Enable the plugin to add Media tracks in Sequencer.
- Add a Media Track to a sequence, create sections referencing media sources and optional `UMediaSoundComponent` for audio.
- Use property tracks when you want to target an existing `UMediaPlayer` on an actor rather than spawning components.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
