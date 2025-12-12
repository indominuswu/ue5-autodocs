# Legacy - Linear Timecode Reader Plugin Overview

## 1. What this plugin does
- Provides a component to decode linear timecode (LTC) from a media source audio track.
- Intended for legacy/simple timecode reading without synchronization support.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users add `ULinearTimecodeComponent` to actors to decode LTC from media audio streams for timecode readout.

## 3. Key Modules
- **LinearTimecode** (Runtime) - Implements the component, decoder, and supporting utilities.

## 4. Important Types & APIs
### `ULinearTimecodeComponent`
- Role: Actor component that reads LTC from an attached media source/audio component and produces frame timecode.
- Key properties: media source/audio input, expected frame rate, drop-frame handling.

### `FLinearTimecodeDecoder`
- Role: Decoder that converts audio samples into timecode values (supports drop-frame via `FDropTimecode`).

### `FMediaAudioSampleReader`
- Role: Helper for pulling audio samples used by the decoder.

## 5. Typical usage patterns
- Enable the plugin and add `LinearTimecodeComponent` to an actor that has access to the media audio stream.
- Configure frame rate and input source; read decoded timecode from the component for synchronization/monitoring.

## 6. Version-specific notes (UE 5.7)
- Labeled “Legacy” in UE 5.7; no other explicit version notes.

