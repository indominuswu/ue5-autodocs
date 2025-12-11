# Asset Registry Export Plugin Overview

## 1. What this plugin does

- Provides a commandlet (`AssetRegistryExport`) to convert an asset registry file into a SQLite database or CSV files.
- Builds per-class tables of asset metadata (tags) plus a global `Assets` table; optionally reports dependency sizes for selected primary asset types.
- Supports dependency listing and size breakdown with optional shared dependency output.
- Disabled by default.

## 2. Key Modules

- **AssetRegistryExport** (Editor, Default)  
  - Role: Implements the export commandlet; depends on `SQLiteCore`.  
  - Notable types: `UAssetRegistryExportCommandlet`, `LogAssetRegistryExport`.

## 3. Important Types & APIs

### `UAssetRegistryExportCommandlet`

- Role: Entry point for exporting an asset registry to SQLite/CSV.  
- Parameters (main ones):  
  - `-Input=<AssetRegistry>` (required)  
  - `-Output=<DbPath>` (SQLite) or `-CSV=<Dir>` (CSV output; creates many files)  
  - `-FilterToClass=<ClassPath>` to limit tables  
  - `-ListDependencies=TypeA,TypeB` to emit dependency CSVs for primary asset types; `-IncludeSharedWithDependencies` to include shared rows  
  - Uses asset registry metadata (size tags) when present.
- Behavior:  
  - Enumerates assets, unions class tag sets, builds per-class tables; sanitizes tag names.  
  - Inserts asset rows (with size tags if present) and writes dependency summaries; uses pragma tweaks for faster SQLite writes.  
  - Reports orphaned assets if size metadata is missing or ambiguous.

## 4. Typical usage patterns

- Run from command line: `UE4Editor-Cmd.exe <Project> -run=AssetRegistryExport -Input=Path/DevelopmentAssetRegistry.bin -Output=Assets.db`  
  - Or `-CSV=OutputDir` for CSVs.  
  - Use `-ListDependencies=TypeA,TypeB` to generate dependency reports (`ListedDependencies.csv`, `SizeDependencies.csv`), optionally `-IncludeSharedWithDependencies`.
- Ensure `WriteBackMetadataToAssetRegistry` is enabled if compressed size tags are needed.

## 5. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted; commandlet behavior reflects the current 5.7 source.
