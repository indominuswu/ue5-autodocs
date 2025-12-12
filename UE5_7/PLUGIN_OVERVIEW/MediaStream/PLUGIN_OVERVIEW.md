# Media Stream Plugin Overview

## 1. What this plugin does
- Experimental chainable media proxy layer that routes media through scheme and object handlers before playback.
- Provides runtime actors/components to host media pipelines that can be configured in Blueprints or details panels.
- Integrates with Media Player assets, allowing managed playback of files, assets, and subobjects via custom scheme handlers.
- Editor module supplies details customizations and widgets for configuring streams, tracks, and playback controls.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor widgets/details plus runtime actors/components and Blueprint helpers for media stream playback.

## 3. Key Modules
- **MediaStream** (Runtime)
  - Role: Core runtime for stream sources, scheme/object handlers, player integration, and Blueprint helpers.
  - Notable types: `UMediaStreamComponent`, `AMediaStreamActor`, `UMediaStreamSource`, `UMediaStreamSchemeHandlerSubsystem`, `UMediaStreamObjectHandlerSubsystem`, `UMediaStreamSourceBlueprintLibrary`, `UMediaStreamPlayerConfig`.
- **MediaStreamEditor** (Editor)
  - Role: Details customizations, Sequencer helpers, and Slate widgets for editing media stream assets and playback controls.
  - Notable types: `FMediaStreamEditorModule`, `MediaStreamSourceCustomization`, `SMediaStreamPlaybackControls`, `SMediaStreamMediaDetails`.

## 4. Important Types & APIs
### `UMediaStreamSource`
- Role: Configurable source definition that links a target media object, scheme handler, and playback options.
- Key properties: player configuration (`FMediaStreamPlayerConfig`), optional texture overrides (`FMediaStreamTextureConfig`), and handler names.

### `UMediaStreamComponent` / `AMediaStreamActor`
- Role: Actor and component wrappers that own a `UMediaStreamSource`, manage playback lifecycle, and expose Blueprint callable controls.
- Typical functions: start/stop playback, update stream source at runtime, query status.

### `UMediaStreamSchemeHandlerSubsystem` / `UMediaStreamObjectHandlerSubsystem`
- Role: Engine subsystems that register and route `IMediaStreamSchemeHandler` and `IMediaStreamObjectHandler` implementations.
- Built-in handlers: file, asset, subobject, and managed schemes; object handlers for media sources, playlists, and nested streams.

### `UMediaStreamSourceBlueprintLibrary`
- Role: Blueprint helpers to create or configure stream sources and set scheme/object handler names without C++.

## 5. Typical usage patterns
- Enable the experimental plugin. Add an `AMediaStreamActor` or `UMediaStreamComponent` to a level.
- Create a `UMediaStreamSource` asset or configure the component inline, selecting a scheme (file, asset, managed) and playback settings.
- Use Blueprint or C++ to start/stop playback and to swap sources. Handlers resolve URIs to concrete media objects for the Media Player.
- In the editor, use the custom details/Sequencer widgets (`SMediaStreamPlaybackControls`, `SMediaStreamMediaTrack`) to scrub media and adjust tracks.

## 6. Version-specific notes (UE 5.7)
- Marked Experimental in the `.uplugin`. No additional UE 5.7-only notes found; behavior is based on the current source tree.
