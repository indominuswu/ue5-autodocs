# Spatialization Plugin Overview

## 1. What this plugin does
- Provides basic spatialization solutions (e.g., interaural time difference) for positioning 3D audio.
- Includes editor support for creating spatialization source settings assets.

## 2. Key Modules
- **Spatialization** (Runtime)
  - Role: Implements spatialization plugins and settings assets used by the audio engine.
  - Notable types: `UITDSpatializationSourceSettings`.
- **SpatializationEditor** (Editor)
  - Role: Editor factory support for creating spatialization source settings assets.
  - Notable types: `UITDSpatializationSettingsFactory`.

## 3. Important Types & APIs
- `UITDSpatializationSourceSettings` (extends `USpatializationPluginSourceSettingsBase`)
  - Role: Asset describing interaural time difference spatialization parameters for a source.
- `UITDSpatializationSettingsFactory`
  - Role: Editor factory that creates `UITDSpatializationSourceSettings` assets via the content browser.

## 4. Typical usage patterns
- Enable the plugin, then create ITD spatialization source settings assets in the content browser.
- Assign the created settings to audio components or sources that should use ITD spatialization.
- Combine with other audio plugins (e.g., soundfields, reverb) for full spatial audio pipelines.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
