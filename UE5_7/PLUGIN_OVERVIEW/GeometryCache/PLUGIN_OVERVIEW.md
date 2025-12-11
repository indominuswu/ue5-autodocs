# Geometry Cache Plugin Overview

## 1. What this plugin does

- Adds runtime support for playing cached mesh animations (Geometry Cache assets) and exposing them as actors/components.
- Provides editor tooling to import, preview, and author Geometry Cache assets and hook them into Sequencer tracks.
- Includes a Niagara renderer for geometry caches and a streaming path for large caches.
- Supplies track types and editors so Geometry Caches can be animated within Level Sequences.

## 2. Key Modules

- **GeometryCache** (Runtime)  
  - Role: Core runtime playback of geometry cache assets, codecs, tracks, and Niagara renderer integration.  
  - Notable types: `UGeometryCache`, `UGeometryCacheComponent`, `AGeometryCacheActor`, `UGeometryCacheCodecBase` (+ Raw/V1), `UGeometryCacheTrackFlipbookAnimation`, `UGeometryCacheTrackStreamable`, `UGeometryCacheTrackTransformAnimation`, `UGeometryCacheStreamingManagerBase`, `UNiagaraGeometryCacheRendererProperties`.

- **GeometryCacheEd** (Editor)  
  - Role: Asset factories, actor factories, thumbnail renderers, and the Geometry Cache asset editor UI/timeline.  
  - Notable types: `UActorFactoryGeometryCache`, `UAssetDefinition_GeometryCache`, `FGeometryCacheAssetEditorToolkit`, `FGeometryCacheTimeSliderController`, Slate timeline widgets.

- **GeometryCacheSequencer** (Editor)  
  - Role: Sequencer integration that adds a Geometry Cache track editor.  
  - Notable types: `FGeometryCacheTrackEditor`.

- **GeometryCacheTracks** (Runtime)  
  - Role: MovieScene track/section types for Geometry Cache playback in sequences.  
  - Notable types: `UMovieSceneGeometryCacheTrack`, `UMovieSceneGeometryCacheSection`, `FMovieSceneGeometryCacheTemplate`.

- **GeometryCacheStreamer** (Editor)  
  - Role: Interfaces and settings for streaming geometry cache data.  
  - Notable types: `IGeometryCacheStreamer`, `IGeometryCacheStream`, `UGeometryCacheStreamerSettings`.

## 3. Important Types & APIs

### `UGeometryCache` / `UGeometryCacheComponent` / `AGeometryCacheActor`

- Role: Asset/component/actor trio for playing back mesh samples over time in-game or in-editor.
- Key properties: Assigned Geometry Cache, playback speed/looping, manual/auto start, sample track selection.
- Key functions: Play/pause/stop, set playback position, query duration and track names.

### `UGeometryCacheTrack*` classes

- Role: Define how mesh samples are organized (flipbook, streamable, transform animation/group).
- Key properties: Sample data sets, motion vectors, frame timing; streamable tracks support chunked loading.

### `UGeometryCacheCodecBase` and derived codecs

- Role: Encode/decode compressed geometry cache data (raw or versioned codecs) for storage and streaming.

### `UNiagaraGeometryCacheRendererProperties`

- Role: Niagara renderer that renders Geometry Cache assets from Niagara systems.
- Key properties: Geometry Cache asset/attribute bindings, material overrides.

### `UMovieSceneGeometryCacheTrack` / `UMovieSceneGeometryCacheSection`

- Role: Sequencer track and sections that bind an actor/component to Geometry Cache playback over time.
- Key properties: Cache asset reference, playback settings per section.

## 4. Typical usage patterns

- Import or create a Geometry Cache asset, then place an `AGeometryCacheActor` or add `UGeometryCacheComponent` to an actor; assign the cache and configure looping/play rate.
- In Sequencer, add a Geometry Cache track to animate cache playback, swapping caches or trimming playback ranges via sections.
- Use the Geometry Cache asset editor to scrub, preview, and edit cache timing; leverage timeline widgets for per-sample inspection.
- For Niagara effects, add a Geometry Cache renderer to emit cached mesh animation within particle systems.
- When handling large caches, configure streaming through `UGeometryCacheStreamerSettings` and streamable tracks.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
