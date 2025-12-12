# Electra Player Plugin Overview

## 1. What this plugin does
- Cross-platform media player supporting local files and internet streaming using the Electra pipeline.
- Provides an optimized Protron path for desktop MP4 playback.
- Exposes editor/import factories to create media player assets bound to Electra.
- Disabled by default; enable when using Electra playback instead of the legacy media player.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users create Electra/Protron media player assets via the factory and use them in Media Framework for playback of files/streams.

## 3. Key Modules
- **ElectraPlayerPluginHandler** (RuntimeNoCommandlet) — Registers the plugin with the media framework.
- **ElectraPlayerRuntime** (RuntimeNoCommandlet) — Core Electra playback runtime.
- **ElectraPlayerPlugin** (RuntimeNoCommandlet) — Media player implementation binding into UE’s media framework.
- **ElectraPlayerFactory** (Editor / RuntimeNoCommandlet) — Media player asset factory and runtime registration.
- **ElectraProtron** (RuntimeNoCommandlet) — Optimized local MP4 (Protron) playback path.
- **ElectraProtronFactory** (Editor / RuntimeNoCommandlet) — Factory/registration for Protron player assets.

## 4. Important Types & APIs

### Player settings
- `UElectraProtronFactorySettings`: Settings struct for Protron factory configuration.

### Components/Helpers
- `URLFragmentComponent`: Utility component for handling URL fragments used by the player stack.

## 5. Typical usage patterns
- Enable the plugin and create an Electra Player asset via the Media Player factory (or Protron variant for MP4-focused playback).
- Use media player assets in Media Framework workflows (Media Player + Media Texture/Material).
- For desktop MP4 optimization, select the Protron player when creating the asset; configure Protron factory settings as needed.
- Combine with `ElectraCodecs`, `ElectraCDM`, and `ElectraSubtitles` as required by the media pipeline.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; overview reflects current source modules.

