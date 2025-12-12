# ChaosCaching Plugin Overview

## 1. What this plugin does

- Adds Chaos Cache assets that record and replay physics simulations.
- Provides runtime support for cache playback and editor tools for recording/authoring caches.
- Integrates with Sequencer and track recorders for capturing simulation data.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Supplies editor cache recording tools/Sequencer integration and runtime playback components for Chaos simulations.

## 3. Key Modules

- **ChaosCaching** (Runtime)  
  - Role: Runtime cache assets, cache adapters for components, and playback management.
- **ChaosCachingEditor** (Editor)  
  - Role: Editor UI, Sequencer track recorder integration, and authoring tools for Chaos Cache assets.

## 4. Important Types & APIs

- `ACacheManagerActor` (ChaosCaching module)  
  - Role: Actor holding cache playback components and `UBillboardComponent` helper; manages observed components via cache adapters.
- Cache adapters such as `FGeometryCollectionComponentCacheAdapter`, `FStaticMeshComponentCacheAdapter`  
  - Role: Bridge component simulation data into cache recording/playback.
- `UMovieSceneChaosCacheTrackRecorder` (ChaosCachingEditor module)  
  - Role: Sequencer track recorder settings for capturing cache data.

## 5. Typical usage patterns

- Place a `CacheManagerActor` and assign components to record; run simulations and record to Chaos Cache assets.
- Use Sequencer with the Chaos Cache track recorder to capture physics simulations during a take.
- Play back recorded caches in-game or in-editor to reproduce deterministic simulation results without re-simulating.

## 6. Version-specific notes (UE 5.7)

- Plugin is experimental and disabled by default in this UE 5.7 build.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
