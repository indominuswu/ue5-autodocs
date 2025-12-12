# MetaHuman Live Link Plugin Overview

## 1. What this plugin does
- Provides Live Link sources and utilities for streaming real-time MetaHuman animation, audio, and face capture data.
- Includes built-in discovery for Live Link Face, local sources, and editor tooling for source/subject settings.
- Integrates with MetaHuman-specific smoothing, media sampling, and Blueprint-accessible local sources.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Live Link sources with editor configuration widgets and Blueprint/local source helpers for MetaHuman streaming.

## 3. Key Modules
- **MetaHumanLiveLinkSource** (Runtime)
  - Role: MetaHuman-specific Live Link subject settings and smoothing processors.
  - Notable types: `UMetaHumanLiveLinkSubjectSettings`, `UMetaHumanSmoothingPreProcessor`, `FMetaHumanLiveLinkSourceStyle`.
- **MetaHumanLiveLinkSourceEditor** (Editor)
  - Role: Editor utilities for configuring MetaHuman Live Link sources.
- **MetaHumanLocalLiveLinkSource** (Runtime)
  - Role: Local Live Link source that supports audio/video subjects and media sampling for MetaHumans.
  - Notable types: `UMetaHumanLocalLiveLinkSource`, `UMetaHumanLocalLiveLinkSubject`, `UMetaHumanLocalLiveLinkSourceBlueprint`, `UMetaHumanAudioBaseLiveLinkSubject`, `UMetaHumanVideoBaseLiveLinkSubject`, `UMetaHumanMediaSamplerLiveLinkSubject`.
- **MetaHumanLocalLiveLinkSourceEditor** (Editor)
  - Role: Editor widgets/monitoring for local sources.
- **LiveLinkFaceSource** (Runtime) / **LiveLinkFaceSourceEditor** (Editor) / **LiveLinkFaceDiscovery** (Runtime)
  - Role: Live Link Face source support and discovery utilities.

## 4. Important Types & APIs
### `UMetaHumanLiveLinkSubjectSettings`
- Role: MetaHuman-specific Live Link subject settings (retargeting options, smoothing via `UMetaHumanSmoothingPreProcessor`).

### `UMetaHumanLocalLiveLinkSource` / `UMetaHumanLocalLiveLinkSourceBlueprint`
- Role: Blueprint-friendly local source for streaming MetaHuman data without external devices.
- Key properties: audio/video subject settings (`UMetaHumanAudioLiveLinkSourceSettings`, `UMetaHumanVideoLiveLinkSourceSettings`), monitor widgets for debugging.

### Live Link Face integration
- `ULiveLinkFaceSource` and discovery helpers stream data from Live Link Face apps into MetaHuman pipelines.

## 5. Typical usage patterns
- Enable the plugin. In the Live Link panel, add MetaHuman Local Source or Live Link Face source.
- Configure subject settings (audio/video smoothing, retarget options) using MetaHuman Live Link subject settings classes.
- In Blueprints, create a `MetaHuman Local Live Link Source` actor/component to emit local animation/audio data for MetaHumans.
- Monitor subjects via the provided editor widgets to verify incoming frames and connection status.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin is not enabled by default.
