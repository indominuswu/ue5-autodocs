# NiagaraSimCaching Plugin Overview

## 1. What this plugin does

- Adds sequencer/take-recorder support for recording and playing back Niagara simulations.
- Provides runtime modules for cache playback and editor tools for authoring cache tracks.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Exposes “Niagara Cache” sequencer tracks/sections (`UMovieSceneNiagaraCacheTrack`/`Section`) and take recorder support that artists use to record/play back Niagara sims.

## 3. Key Modules

- **NiagaraSimCaching** (Runtime) – Runtime cache system, logging (`LogNiagaraSimCaching`), and Niagara-specific sequencer section/track types.
- **NiagaraSimCachingEditor** (Editor) – Editor styles and track editors for sequencer/take recorder integration.

## 4. Important Types & APIs

### `INiagaraSimCachingPlugin`

- Module interface exposing `Get()`/`IsAvailable()` for the runtime cache module.

### Sequencer cache tracks (`UMovieSceneNiagaraCacheTrack`, `UMovieSceneNiagaraCacheSection`)

- Sequencer track/section types that drive recorded Niagara cache playback within movie scenes.

### Track editing helpers (`UNiagaraCacheTrackEditor`, `UMovieSceneNiagaraTrackRecorder`)

- Editor classes that register the cache track, manage UI, and handle recording Niagara simulations into cache assets.

## 5. Typical usage patterns

- Enable the plugin, add a “Niagara Cache” track in Sequencer to record or play back a Niagara system.
- Use the take recorder integration to capture live Niagara simulations; playback uses the generated cache through the `UMovieSceneNiagaraCacheSection`.
- Runtime playback uses the NiagaraSimCaching module; editor-only styles and track editors are loaded in the editor.

## 6. Version-specific notes (UE 5.7)

- No explicit 5.7-specific notes detected; behavior follows the current module code.

