# Music Environment Plugin Overview

## 1. What this plugin does
- Provides a project-wide source of musical timing info (clocks, metronome, events) for audio systems.
- Manages clock sources and metronome spawning via an engine subsystem.
- Includes supporting musical data types (maps, handles, enums, assets) for synchronized music interactions.
- Ships optional editor customizations for musical time signature inputs.

## 2. Key Modules
- **MusicEnvironment** (Runtime)
  - Role: Core music timing subsystem and supporting types.
  - Notable types: `UMusicEnvironmentSubsystem`, `UMusicClockSourceManager`, `IMusicEnvironmentMetronome`, `UMusicEnvironmentClockSource`, `UMusicEnvironmentMetronome`, musical asset/map/handle structs.
- **MusicEnvironmentEditor** (Editor)
  - Role: Editor widgets and customizations for musical time signatures.
  - Notable types: `SMusicEnvironment` time signature inputs (`SFrameBasedTimeSignatureInput` customization).
- **MusicEnvironmentTests** (UncookedOnly)
  - Role: Test scaffolding for the music environment systems.

## 3. Important Types & APIs

### `UMusicEnvironmentSubsystem`
- Role: Engine subsystem providing access to clock sources and metronome spawning.
- Key functions: `Get()` singleton access, `GetClockSourceManager`, `SetMetronomeClass`, `CanSpawnMetronome`, `SpawnMetronome`.
- Data: holds `UMusicClockSourceManager` and configurable metronome class.

### `UMusicClockSourceManager`
- Role: Manages available music clock sources; used by the subsystem to provide synchronized clocks.

### `IMusicEnvironmentMetronome` / `UMusicEnvironmentMetronome`
- Role: Interface and default implementation for ticking musical time and emitting beats/events.

### Musical data types
- `FMusicMapSource`, `FMusicHandle`, `FMusicAsset`, enums and frame-based map structures to describe tempo/time signatures and mapped events.

## 4. Typical usage patterns
- Enable the plugin, then access `UMusicEnvironmentSubsystem::Get()` to manage clock sources or spawn a metronome.
- Configure a metronome class (project-specific implementation) via `SetMetronomeClass`; query `CanSpawnMetronome` before spawning.
- Use musical map/asset types to drive synchronized audio events; integrate clocks with audio gameplay logic.
- In editor tools, use the provided time signature input widget/customization for authoring frame-based signatures.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; functionality is based on the current source layout.
