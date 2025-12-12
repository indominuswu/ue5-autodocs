# Electra Player Subtitle Module Plugin Overview

## 1. What this plugin does
- Supplies subtitle decoding and rendering support for the Electra media player.
- Handles subtitle track parsing for streams played through Electra.
- Disabled by default; enable when using Electra with subtitle tracks.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users enable it to get subtitle track decoding/rendering when selecting subtitles in Electra media players.

## 3. Key Modules
- **ElectraSubtitles** (RuntimeNoCommandlet)  
  - Role: Subtitle decoder module for Electra playback.

## 4. Important Types & APIs
- Subtitle parsing and rendering are internal to the module; no Blueprint-facing classes are exposed.
- Integrates with Electra media player instances to present subtitle tracks.

## 5. Typical usage patterns
- Enable alongside `ElectraPlayer` when playing content that includes subtitle tracks.
- Select subtitle tracks through the media player interface; ElectraSubtitles handles decoding/rendering.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; functionality is based on the current source.

