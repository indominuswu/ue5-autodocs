# Harmonix Plugin Overview

## 1. What this plugin does
- Provides a suite of Harmonix audio features: DSP effects, MIDI parsing, tempo/clock utilities, and Metasound nodes.
- Supplies runtime components and data types for music-driven gameplay, offline rendering, and audio analysis.
- Includes editor modules for authoring/testing MIDI and Metasound graphs built on Harmonix data.

## 2. Key Modules
- **Harmonix** (Runtime)  
  - Role: Core Harmonix utilities, plugin/developer settings, timebase helpers.
- **HarmonixDsp** (Runtime)  
  - Role: DSP engine, audio buffers, gain/panner, stretching/pitch shifting, filters, analysis helpers.
- **HarmonixMidi** (Runtime)  
  - Role: MIDI file parsing, events, song/tempo maps, Blueprint-facing MIDI data.
- **HarmonixMetasound** (Runtime)  
  - Role: Metasound nodes/data types for Harmonix music assets, MIDI streams, transport control, and analysis.
- **HarmonixEditor**, **HarmonixDspEditor**, **HarmonixMidiEditor**, **HarmonixMetasoundEditor** (UncookedOnly)  
  - Role: Editor-time registration, testing, and utilities for the corresponding runtime modules.
- **HarmonixDspTests**, **HarmonixMidiTests**, **HarmonixMetasoundTests** (UncookedOnly)  
  - Role: Test harness modules.

## 3. Important Types & APIs

### Core settings
- `UHarmonixDeveloperSettings`, `UHarmonixPluginSettings`: Configure global behavior for Harmonix audio systems.

### Runtime components and subsystems
- `UMusicClockComponent`, `UMusicTempometerComponent`, `UMusicClockDriverBase`: Actor components providing tempo/transport clocks for gameplay.
- `UMetasoundOfflinePlayerComponent`: Plays Metasound assets offline for rendering/preview.
- `UMidiClockUpdateSubsystem`: Subsystem that coordinates MIDI/clock updates across worlds.

### Data types and utilities
- Harmonix DSP: `FHarmonixDspAudioBuffer`, `FStretcherAndPitchShifter`, `FPanner`, and associated settings structs for filters, distortion, delay, vocoder, etc.
- Harmonix MIDI: `FMidiFile`, `FMidiTrack`, `FMidiEvent`, `FBeatMap`, `FTempoMap`, `FSongMaps`, plus Blueprint-friendly `FMidiNote`.
- Harmonix Metasound: Data types such as `FHarmonixMetasoundMusicAsset`, `FMidiStream`, `FMidiClock`, `FMusicTransport`, `FMusicTimeInterval`, and nodes like `MidiPlayerNode`, `MusicSeekTargetBuilder`, `DelayNode`, `MorphingLfoNode`, `TransportWavePlayerControllerNode`.
- Blueprint helpers: `UMusicParameterBlueprintLibrary` for manipulating music parameters inside graphs.

## 4. Typical usage patterns
- Enable the plugin, then add `MusicClockComponent`/`MusicTempometerComponent` to actors needing tempo-synced behavior.
- Import or generate MIDI assets and use Harmonix MIDI data with Metasound nodes (`MidiPlayerNode`, `MidiStream` analyzers) to drive audio/gameplay.
- Use Harmonix DSP nodes for stretching, pitch shifting, filtering, and analysis inside Metasound or custom pipelines.
- Configure global behavior via Harmonix plugin/developer settings; use editor modules to test MIDI playback or Metasound graphs.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
