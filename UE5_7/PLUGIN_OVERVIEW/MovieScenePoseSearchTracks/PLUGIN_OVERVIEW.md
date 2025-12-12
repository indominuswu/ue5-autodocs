# Movie Scene Pose Search Tracks Plugin Overview

## 1. What this plugin does
- Adds Sequencer track types that work with pose-search-driven animation stitching.
- Provides runtime systems to evaluate stitch animation sections and their pose data.
- Includes editor support for creating and editing stitch tracks.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Sequencer users add the Stitch Anim track/sections and rely on the editor track editor plus runtime systems to play pose-search-driven animation.

## 3. Key Modules
- **MovieScenePoseSearchTracks** (Runtime)
  - Role: Runtime track/section types and systems for pose-search stitch animation.
  - Notable types: `UMovieSceneStitchAnimTrack`, `UMovieSceneStitchAnimSection`, `UMovieSceneStitchAnimSystem`, `FPoseSearchTracksComponentTypes`.
- **MovieScenePoseSearchTracksEditor** (Editor)
  - Role: Sequencer track editor support for stitch animation tracks.
  - Notable types: `FStitchAnimTrackEditor`.

## 4. Important Types & APIs

### `UMovieSceneStitchAnimTrack` / `UMovieSceneStitchAnimSection`
- Role: Sequencer track and sections that reference pose-search-driven stitch animation data.
- Key properties: pose search assets/sections (configured per section), section timing.

### `UMovieSceneStitchAnimSystem`
- Role: Runtime system that evaluates stitch sections and updates bound components during playback.

### `FPoseSearchTracksComponentTypes`
- Role: Component type definitions used by the systems when evaluating pose-search data.

## 5. Typical usage patterns
- Enable the plugin and add a Stitch Anim track in Sequencer to drive pose-search-based animation snippets.
- Author sections referencing pose search data; the runtime system evaluates sections during sequence playback.
- Use the editor track tools (provided by the editor module) to add, move, or configure stitch sections.

## 6. Version-specific notes (UE 5.7)
- Plugin is experimental; no additional UE 5.7-specific notes were found beyond current source comments.

