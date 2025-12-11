# Replay Tracks (Experimental) Plugin Overview

## 1. What this plugin does
- Adds MovieScene tracks/sections for playing recorded gameplay replays inside sequences.
- Provides a global replay manager and broker interface to coordinate replay control per world.
- Includes editor track support for sequencing replay playback.

## 2. Key Modules
- **ReplayTracks** (Runtime)  
  - Runtime replay track evaluation, replay manager, and sequencing system.
- **ReplayTracksEditor** (Editor)  
  - Track editor integration and asset registration for replay tracks/sections in Sequencer.

## 3. Important Types & APIs
### `FMovieSceneReplayManager`
- Role: Global utility managing replay status; arms/disarms replay and routes control to registered brokers.
- Functions: `RegisterBroker`/`UnregisterBroker`, `FindBroker`, `ArmReplay`, `DisarmReplay`, `GetReplayStatus`.

### `FMovieSceneReplayBroker`
- Role: Game-specific hook for replay operations; override `CanStartReplay`, `OnReplayStarted/Stopped`, `OnGoToTime`, `OnReplayPlay/Pause`.
- Brokers are registered with the manager and selected per world.

### `UMovieSceneReplayTrack` / `UMovieSceneReplaySection`
- Role: Sequencer track/section types representing replay playback; evaluated by `UMovieSceneReplaySystem`.

## 4. Typical usage patterns
- Enable the plugin (experimental) and add a Replay track in Sequencer.
- Implement a custom `FMovieSceneReplayBroker` for your game to handle actual replay start/seek/pause logic.
- Register the broker at startup; the Replay track drives `FMovieSceneReplayManager` which delegates to the broker for the active world.

## 5. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`; no additional UE 5.7-specific changes surfaced in source.

