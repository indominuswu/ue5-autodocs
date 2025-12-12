# Media Framework Utilities Plugin Overview

## 1. What this plugin does

- Utility assets and actors that simplify Media Framework setup, profiling, and time-synchronization workflows.
- Provides Media Bundle assets, proxy sources/outputs, and profile management for multi-device configurations.
- Includes Blueprint helpers and editor tooling for configuring media profiles on supported desktop platforms.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Media bundle/profile assets, proxy sources/outputs, Blueprint helpers, and editor configuration tools.

## 3. Key Modules

- **MediaFrameworkUtilities** (Runtime; Win64/Linux/Mac)
  - Role: Core runtime types for media bundles, profiles, proxy assets, and time-sync sources.
  - Notable types: `UMediaBundle`, `AMediaBundleActorBase`, `UMediaBundleTimeSynchronizationSource`, `UMediaPlayerTimeSynchronizationSource`, `UMediaProfile`, `UMediaProfilePlaybackManager`, `UMediaProfileSettings`, `UMediaProfileBlueprintLibrary`, `UProxyMediaSource`, `UProxyMediaOutput`.
- **MediaFrameworkUtilitiesEditor** (Editor; Win64/Linux/Mac)
  - Role: Editor integration for creating/configuring the above assets and profiles.

## 4. Important Types & APIs

### `UMediaBundle` / `AMediaBundleActorBase`

- Role: Package a media source, media player, and related components into a reusable asset and actor wrapper.
- Behavior: Simplifies placing media-driven actors in a level and managing their lifecycle.

### `UMediaProfile`, `UMediaProfileSettings`, `UMediaProfilePlaybackManager`

- Role: Define and manage media device profiles (sources/outputs) for a project.
- Key behaviors: Select active profiles, manage switching, and expose profile settings to the editor.

### `UMediaProfileBlueprintLibrary`

- Role: Blueprint-accessible helpers to get/set active media profiles at runtime.

### `UProxyMediaSource` / `UProxyMediaOutput`

- Role: Proxy assets that redirect to different underlying sources/outputs based on the active media profile.

### `UMediaBundleTimeSynchronizationSource` / `UMediaPlayerTimeSynchronizationSource`

- Role: Time synchronization sources for media playback, integrating with UE time-synchronization frameworks.

## 5. Typical usage patterns

- Create a Media Bundle asset to package a media source/player; place `AMediaBundleActorBase` derivatives in levels for playback.
- Define Media Profiles for different ingest/output setups and use proxy sources/outputs so assets automatically follow the active profile.
- Use Blueprint helpers or profile manager to switch profiles at runtime; employ time-sync sources when aligning media to an external clock.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
