# Cinematic Prestreaming Plugin Overview

## 1. What this plugin does

- Records streaming requests during cinematic sequences and replays them to pre-stream data during gameplay/rendering.
- Provides editor tooling to generate prestreaming assets from sequences and maps.
- Integrates with Movie Pipeline to automate prestreaming asset creation.

## 2. Key Modules

- **CinematicPrestreaming** (Runtime)  
  - Role: Runtime support for recorded prestreaming playback during cinematics.
- **CinematicPrestreamingEditor** (UncookedOnly)  
  - Role: Editor subsystem and UI for recording/creating prestreaming assets.
  - Notable types: `UCinePrestreamingEditorSubsystem`, `FCinePrestreamingGenerateAssetArgs`.

## 3. Important Types & APIs

### `UCinePrestreamingEditorSubsystem`
- Role: Editor subsystem that drives generation of prestreaming assets via Movie Pipeline executors.
- Key functions: `IsRendering`, `GeneratePrestreamingAsset`, `CreatePackagesFromGeneratedData`, delegates (`OnAssetGenerated`) for build completion.
- Inputs: `FCinePrestreamingGenerateAssetArgs` (output directory, level sequence path, map, resolution).

### `FCinePrestreamingGenerateAssetArgs`
- Role: Arguments for creating prestreaming assets, including output path, target sequence, map, and resolution overrides.

## 4. Typical usage patterns

- Enable the plugin, open the editor, and use the Cinematic Prestreaming subsystem to record streaming requests from a sequence.
- Invoke `GeneratePrestreamingAsset` with the target sequence/map to run Movie Pipeline and emit prestreaming data.
- Use `CreatePackagesFromGeneratedData` to package generated prestreaming assets for runtime playback.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
