# Interchange OpenUSD Plugin Overview

## 1. What this plugin does

- Adds OpenUSD translation to the Interchange framework for importing USD scenes and assets.
- Provides an Interchange pipeline tuned for USD payloads plus editor customization for translator settings.
- Depends on the USDCore plugin and other Interchange extensions.
- Experimental and disabled by default.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users enable this to import USD via Interchange, configure `UInterchangeUsdTranslatorSettings` in the import dialog, and run the USD-specific pipeline.

## 3. Key Modules

- **InterchangeOpenUSDImport** (Runtime, Default) — USD translator, pipeline, and context helpers.
- **InterchangeOpenUSDEditor** (Editor, Default) — Details customization for translator settings and editor integration.
- Plugin dependencies: `Interchange`, `InterchangeEditor` (Editor/Program), `InterchangeOpenVDB` (Editor), `USDCore`.

## 4. Important Types & APIs

### `UInterchangeUSDTranslator`

- Role: Interchange translator for USD sources; implements `Translate`, `CanImportSourceData`, and settings handling.
- Uses `UInterchangeUsdTranslatorSettings` for per-import options; internally backed by an implementation helper.

### `UInterchangeUsdPipeline`

- Role: Pipeline for processing USD-imported node containers, handling post-factory/post-import steps for USD-specific assets.
- Executes post-factory hooks to adjust created assets after translation.

### `UInterchangeUsdContext`

- Role: USD-specific context object managing info caches and shared state during USD import.

### Editor customization

- `FInterchangeUsdTranslatorSettingsCustomization` (in editor module) customizes details panels for USD translator settings.

## 5. Typical usage patterns

- Enable the plugin along with Interchange and USDCore. Choose the USD translator during import; settings are exposed through the Interchange import dialog.
- Configure `UInterchangeUsdTranslatorSettings` (via the dialog) for scene variants, payload loading, and other USD options.
- USD assets flow through `UInterchangeUsdPipeline`, which applies USD-specific adjustments during import.

## 6. Version-specific notes (UE 5.7)

- Marked experimental and disabled by default; no additional UE 5.7-specific notes present in the source.

