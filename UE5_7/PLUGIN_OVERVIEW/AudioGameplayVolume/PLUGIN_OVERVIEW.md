# AudioGameplayVolume Plugin Overview

## 1. What this plugin does

- Provides spatial audio gameplay volumes that drive submix sends, reverb, attenuation, and other audio effects.
- Supplies runtime components for mutating audio behavior inside volumes and editor tools for visualization.
- Integrates with the AudioGameplay framework to dispatch parameters and manage volume proxies.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime volume components/mutators (reverb, filter, submix, attenuation) with editor visualizers for authoring audio gameplay regions.

## 3. Key Modules

- **AudioGameplayVolume** (Runtime)  
  - Role: Runtime volume actors/components, mutators, and the audio gameplay volume subsystem.
- **AudioGameplayVolumeEditor** (Editor)  
  - Role: Component visualizers, detail customizations, and editor integration for authoring volumes.

## 4. Important Types & APIs

### `UAudioGameplayVolumeSubsystem` (UAudioEngineSubsystem)

- Role: Tracks registered audio gameplay volume components and updates proxies; entry point for volume queries.
- Key functions: `AddVolumeComponent`, `UpdateVolumeComponent`, `RemoveVolumeComponent`, proxy synchronization.

### `UAudioGameplayVolumeComponent` / `UAudioGameplayVolumeComponentBase` (UAudioGameplayComponent)

- Role: Core volume component that registers with the subsystem and applies audio settings within bounds.
- Key functions: Volume lifecycle handling and parameter dispatch to affected audio.

### `UAudioGameplayVolumeMutator` (UAudioGameplayComponent)

- Role: Base class for mutators that change audio behavior inside a volume.
- Derived mutators: `UReverbVolumeComponent`, `UFilterVolumeComponent`, `USubmixSendVolumeComponent`, `USubmixOverrideVolumeComponent`, `UAttenuationVolumeComponent`.

### `UAudioGameplayVolumeProxy` and derivatives

- Role: Proxy objects representing volume data for efficient runtime queries; supports primitive component proxies.

## 5. Typical usage patterns

- Enable the plugin; place Audio Gameplay Volume actors in the level (or attach `AudioGameplayVolumeComponent` to actors) to define audio regions.
- Choose mutator components (reverb, filter, submix send/override, attenuation) to apply specific audio effects within the volume bounds.
- Use editor visualizers to inspect volume extents and debug audio influence regions.
- Combine with `AudioGameplay` components for parameter dispatch and audio component pooling.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

