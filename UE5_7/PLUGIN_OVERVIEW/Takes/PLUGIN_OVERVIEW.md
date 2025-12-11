# Take Recorder Plugin Overview

## 1. What this plugin does
- Virtual Production take recording suite for capturing actor/scene data, organizing takes, and playing them back.
- Provides recording sources, track recorders, naming token support, and Sequencer integration for LiveLinkHub/editor.
- Includes runtime `TakeMovieScene` support for playing take assets.

## 2. Key Modules
- **TakesCore** (UncookedOnly) – Core take metadata, asset discovery, and Blueprint helpers.
- **TakeTrackRecorders** (UncookedOnly) – Track recorder factories for transforms, particles, visibility, caches, etc.
- **TakeRecorderSources** (UncookedOnly) – Defines recording sources used by Take Recorder.
- **TakeRecorder** (UncookedOnly) – Main recorder UI/logic and user/project settings.
- **TakeMovieScene** (Runtime) – Movie scene types and settings used when playing back recorded takes.
- **TakeSequencer** (Editor) – Sequencer track editor integration.
- **CacheTrackRecorder**, **TakeRecorderNamingTokens** (UncookedOnly) – Auxiliary recorders and naming token implementations.

## 3. Important Types & APIs
- Settings: `UTakeRecorderUserSettings`, `UTakeRecorderProjectSettings` (configurable recording defaults/UI toggles); `UMovieSceneTakeSettings` (asset-level options).
- Metadata: `UTakeMetaData` stored on sequences; `UTakesCoreBlueprintLibrary` to find takes by slate/timecode.
- Recorders: `UMovieSceneTrackRecorder` base with implementations like `UMovieScene3DTransformTrackRecorder`, `UMovieSceneParticleTrackRecorder`, `UMovieSceneVisibilityTrackRecorder`, and cache recorders.
- Track recorder factories (`IMovieSceneTrackRecorderFactory`) map object types to recorder instances.
- Sequencer integration: `FTakeSequencerModule`, `FTemplateSequenceSection` equivalents for take sections, plus track editor registration.

## 4. Typical usage patterns
- Enable the plugin (and dependencies: AudioCapture, LevelSequenceEditor, NamingTokens).
- In the Take Recorder UI, select sources (actors, LiveLink, audio) and start recording; track recorders generate Level Sequence assets with embedded take metadata.
- Use naming tokens to format slate/take names; metadata (take number, slate) is stored on the created sequence.
- Play back takes via Sequencer; runtime uses `TakeMovieScene` types for playback.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; modules are primarily uncooked/editor-focused with runtime playback support.

