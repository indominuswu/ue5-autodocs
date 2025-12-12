# Actor Sequence (Experimental) Plugin Overview

## 1. What this plugin does
- Provides runtime support for embedded actor sequences driven by `UActorSequence` assets.
- Adds a component/section player for attaching a sequence to an actor and playing it back.
- Editor tools for authoring actor sequences and integrating them into Movie Scene.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Offers an editor tab/customizations for authoring actor sequences and runtime component/player APIs to drive playback on actors.

## 3. Key Modules
- **ActorSequence** (Runtime)
  - Role: Runtime sequence asset, component, and player for embedded sequences.
- **ActorSequenceEditor** (Editor)
  - Role: Editor integration, tabs, and customization for actor sequence assets.

## 4. Important Types & APIs

### `UActorSequence`
- Role: Sequence asset containing tracks bound to an actor instance.

### `UActorSequenceComponent`
- Role: Component that owns an `UActorSequence` and a `UActorSequencePlayer` for playback.
- Key functions: start/stop/playback controls via the player, exposes sequence assignment on the component.

### `UActorSequencePlayer`
- Role: Controls playback of the actor sequence (play, pause, scrub, time control).

### Editor classes
- `FMovieSceneSequenceEditor_ActorSequence`, `FActorSequenceEditorTabSummoner`, `UActorSequenceComponentCustomization` provide editor UI and customization.

## 5. Typical usage patterns
- Add `UActorSequenceComponent` to an actor and assign an `UActorSequence` asset.
- Use the component/player to play or control the sequence at runtime or in editor preview.
- Author sequences through the Actor Sequence editor tab; customize component properties via provided detail customization.

## 6. Version-specific notes (UE 5.7)
- Marked experimental in the plugin metadata; no additional UE 5.7-specific notes found.
