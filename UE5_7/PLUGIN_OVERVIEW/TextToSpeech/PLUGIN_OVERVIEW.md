# TextToSpeech Plugin Overview

## 1. What this plugin does

- Provides a cross-platform text-to-speech system with Blueprint access.
- Manages speech channels that can speak, stop, mute, and control audio parameters per channel.
- Ships with platform factories (Android, Apple, Linux, Mac, Windows) and a built-in Flite fallback.

## 2. Key Modules

- **TextToSpeech** (Runtime)
  - Role: Implements the speech engine subsystem, platform factories, and Flite integration.

## 3. Important Types & APIs

### `UTextToSpeechEngineSubsystem`

- Role: Engine subsystem exposing Blueprint functions to manage text-to-speech channels.
- Key functions: `SpeakOnChannel`, `StopSpeakingOnChannel`, `StopSpeakingOnAllChannels`, `IsSpeakingOnChannel`, `Get/SetVolumeOnChannel`, `Get/SetRateOnChannel`, `MuteChannel`, `UnmuteChannel`, `IsChannelMuted`, channel activation helpers, and channel creation via default or custom factories.

### `FTextToSpeechBase` and `ITextToSpeechFactory`

- Role: Abstract speech implementation and factory interface used by platform-specific classes (`AndroidTextToSpeechFactory`, `AppleTextToSpeechFactory`, `LinuxTextToSpeechFactory`, `MacTextToSpeechFactory`, `WindowsTextToSpeechFactory`).

### Flite adapters

- Role: `FFliteTextToSpeech`, `FFliteAdapter`, and related data structures provide an embedded synthesis backend when no platform service is present.

## 4. Typical usage patterns

- Enable the plugin, then access `TextToSpeechEngineSubsystem` from Blueprints or C++.
- Add or activate a channel (e.g., default channel) before invoking `SpeakOnChannel`; adjust volume/rate or mute as needed.
- Use platform-specific factories automatically via the subsystem; Flite provides fallback voices where platform APIs are unavailable.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
