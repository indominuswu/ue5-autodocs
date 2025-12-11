# GeometryCacheLevelSequenceBaker Plugin Overview

## 1. What this plugin does

- Provides an editor tool to bake animated Skeletal Mesh tracks in Level Sequences into Geometry Cache assets.
- Adds UI commands and styles for invoking the bake workflow directly from Sequencer.
- Offers a details customization for configuring bake parameters.

## 2. Key Modules

- **GeometryCacheLevelSequenceBaker** (Editor)  
  - Role: Editor-only baking workflow that converts Level Sequence animation into Geometry Cache data.  
  - Notable types: `FGeometryCacheLevelSequenceBaker`, `FGeometryCacheLevelSequenceBakerCommands`, `FGeometryCacheLevelSequenceBakerCustomization`, `FGeometryCacheLevelSequenceBakerStyle`.

## 3. Important Types & APIs

### `FGeometryCacheLevelSequenceBaker`

- Role: Core utility that traverses a Level Sequence, samples animated skeletal meshes, and outputs a Geometry Cache asset.
- Key settings: Frame range, target asset/output path, compression options (configured via the customization UI).

### `FGeometryCacheLevelSequenceBakerCommands` / `FGeometryCacheLevelSequenceBakerStyle`

- Role: Register editor commands/menus and styling used to expose the bake action inside Sequencer or toolbars.

### `FGeometryCacheLevelSequenceBakerCustomization`

- Role: Details customization for tuning bake parameters before running the conversion.

## 4. Typical usage patterns

- Enable the plugin, open a Level Sequence containing animated Skeletal Mesh tracks, and trigger the “Bake to Geometry Cache” command (exposed by this plugin).
- Adjust bake settings through the provided details customization, then run the baker to generate a new Geometry Cache asset.
- Use the resulting Geometry Cache in Sequencer or as a runtime playback asset where skeletal animation is impractical.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
