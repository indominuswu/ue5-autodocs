# SpeedTree Importer Plugin Overview

## 1. What this plugin does
- Imports SpeedTree runtime files into Unreal as static/foliage assets.
- Provides factories for initial import and reimport flows, preserving SpeedTree metadata.
- Exposes import options through `SpeedTreeImportData` for materials, LODs, and wind settings.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor import/reimport factories (`USpeedTreeImportFactory`, `UReimportSpeedTreeFactory`) and settings (`USpeedTreeImportData`) that artists use to bring SpeedTree assets into Unreal.

## 3. Key Modules
- **SpeedTreeImporter** (Editor)  
  - Role: Import/reimport factories, import data definitions, and module interface for SpeedTree assets.  
  - Notable types: `USpeedTreeImportFactory`, `UReimportSpeedTreeFactory`, `USpeedTreeImportData`, `ISpeedTreeImporter`.

## 4. Important Types & APIs
### `USpeedTreeImportFactory` / `UReimportSpeedTreeFactory`
- Role: Factories that handle importing `.srt` or other SpeedTree runtime files and reimporting updated assets.
- Key behaviors: build mesh/LOD data, apply materials, and configure wind/billboard options from import data.

### `USpeedTreeImportData`
- Role: UObject storing import settings (material overrides, billboard usage, LOD generation, scale/wind options).
- Used to persist settings between imports/reimports.

## 5. Typical usage patterns
- Enable the plugin (on by default) and import a SpeedTree runtime file via the Content Browser; configure options in the import dialog.
- Reimport updated tree assets using `UReimportSpeedTreeFactory` to preserve settings captured in `USpeedTreeImportData`.
- Use resulting assets in foliage tools or as static meshes with SpeedTree-specific material setups.

## 6. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes observed; plugin is stable and enabled by default.

