# Live Link Plugin Overview

## 1. What this plugin does
- Streams animated data (poses, curves, subjects) into Unreal from external sources over the Live Link protocol.
- Provides runtime components and Blueprint libraries to consume Live Link subjects on actors.
- Integrates with Sequencer/MovieScene for recording and playback, and offers editor UI to configure sources and subjects.
- Supports Live Link Hub workflows, virtual subjects, and multi-user aware tooling.

## 2. Key Modules
- **LiveLink** (Runtime)  
  - Core Live Link data model, sources, settings, Blueprint APIs, and broadcast support.  
  - Notable types: `ULiveLinkComponent`, `ULiveLinkBroadcastComponent`, `ULiveLinkBroadcastSubsystem`, `ULiveLinkBlueprintLibrary`, `ULiveLinkSettings`, `ULiveLinkBlueprintVirtualSubject`, `ULiveLinkHubSubjectSettings`.
- **LiveLinkComponents** (Runtime)  
  - Actor-facing controls for binding Live Link subjects to components.  
  - Notable types: `ULiveLinkComponentController`, `ULiveLinkComponentSettings`, `ILiveLinkComponentModule`, `ULiveLinkDataPreviewComponent`.
- **LiveLinkEditor** (Editor)  
  - Details customizations and editor settings for sources, components, and virtual subjects (`ULiveLinkEditorSettings`, `LiveLinkSourceSettingsDetailCustomization`, graph panel pin factories).
- **LiveLinkGraphNode** (UncookedOnly)  
  - Node definitions used for editor graph integration.
- **LiveLinkMovieScene** (Runtime)  
  - Sequencer support for Live Link subjects/tracks.
- **LiveLinkSequencer** (UncookedOnly)  
  - Editor bindings between Live Link and Sequencer.
- **LiveLinkMultiUser** (UncookedOnly)  
  - Multi-user collaboration hooks for Live Link sessions.

## 3. Important Types & APIs

### `ULiveLinkComponent`
- Role: Base component that receives Live Link subject data each tick; exposes transforms/curves to Blueprints.
- Key properties: assigned subject role/type, interpolation settings.

### `ULiveLinkComponentController`
- Role: Extends an actor with binding rules to drive scene components (e.g., skeletal meshes, cameras) from a Live Link subject.
- Key properties: subject preset binding, per-role evaluation settings; uses `ULiveLinkComponentSettings` for defaults.

### `ULiveLinkBroadcastComponent` / `ULiveLinkBroadcastSubsystem`
- Role: Publishes Live Link subject data from the current world over the message bus, configurable via Blueprint.
- Key APIs: multicast delegates for broadcast start/stop; component exposes endpoints and network options.

### `ULiveLinkBlueprintLibrary`
- Role: Blueprint function library for querying subjects, roles, and frame data; used to read transforms/curves in gameplay scripts.

### `ULiveLinkBlueprintVirtualSubject`
- Role: Blueprint-defined virtual subject; combines or transforms other subjects before consumers receive them.

### `ULiveLinkSettings` / `ULiveLinkEditorSettings`
- Role: Developer settings for default subjects, timecode/synchronization, interpolation, and editor UI preferences.

## 4. Typical usage patterns
- Enable Live Link and add a Live Link source (Message Bus, UDP, device, etc.) in the editor Live Link panel.
- Add `ULiveLinkComponent` or `ULiveLinkComponentController` to actors (e.g., cameras, skeletal meshes) and assign the desired subject; controllers map subject data to component properties.
- Use Blueprint nodes from `LiveLinkBlueprintLibrary` to pull transforms/curves at runtime, or preview subjects with `ULiveLinkDataPreviewComponent`.
- Record or play back Live Link data through Sequencer (LiveLinkMovieScene) and use virtual subjects for combining sources.
- For hub workflows, configure hub subject settings and broadcast from in-editor sources via `ULiveLinkBroadcastComponent`.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
