# Sound Module Plugin Overview

## 1. What this plugin does
- Adds playback support for tracker module formats (MOD, S3M, XM, IT).
- Provides asset types and procedural waves to stream module audio at runtime.
- Includes an editor importer and asset type actions for module files.

## 2. Key Modules
- **SoundMod** (Runtime)
  - Role: Runtime playback of module assets and associated sound nodes.
  - Notable types: `USoundMod`, `USoundModWave`, `USoundNodeModPlayer`.
- **SoundModImporter** (Editor)
  - Role: Imports tracker files into `USoundMod` assets and registers asset type actions.
  - Notable types: `USoundModImporterFactory`.

## 3. Important Types & APIs
- `USoundMod` (extends `USoundBase`)
  - Role: Asset representing a tracker module; referenced by wave players and nodes.
- `USoundModWave` (extends `USoundWaveProcedural`)
  - Role: Procedural audio source that streams from a `USoundMod` asset.
- `USoundNodeModPlayer` (extends `USoundNodeAssetReferencer`)
  - Role: SoundCue node to play a module asset in sound graphs.
- `USoundModImporterFactory`
  - Role: Editor factory for importing MOD/S3M/XM/IT files into `USoundMod`.

## 4. Typical usage patterns
- Enable the plugin, then import tracker files via the content browser; the importer creates `USoundMod` assets.
- Use `USoundModWave` or `USoundNodeModPlayer` in SoundCues/Blueprints to play the imported modules.
- Deploy on supported platforms (Win64, Mac, Linux, Android) as defined in the module allowlist.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
