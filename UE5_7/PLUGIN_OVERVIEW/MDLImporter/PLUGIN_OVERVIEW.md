# MDL Importer Plugin Overview

## 1. What this plugin does

- Imports NVIDIA MDL material files into Unreal as materials/material instances.
- Wraps the MDL SDK to load modules, compile materials, and create UE material/texture assets.
- Provides an import options dialog and logging to surface MDL SDK issues during import/reimport.

## 2. Key Modules

- **MDLImporter** (Editor; Win64/Mac/Linux)
  - Role: Full MDL import pipeline, UI, and SDK binding.
  - Notable types: `IMDLImporterModule` (module interface), `FMDLImporter` (core importer), `UMDLImporterOptions`, `SMDLOptionsWindow`, `FMDLMaterialSelector`.

## 3. Important Types & APIs

### `IMDLImporterModule` / `FMDLImporter`

- Role: Module interface that exposes access to the internal importer; `GetMDLImporter()` returns the importer instance used by factories/reimporters.
- Behavior: Loads MDL SDK libraries (platform-specific), manages SDK contexts, and executes import/reimport.

### `UMDLImporterOptions`

- Role: UObject holding importer settings (e.g., extra MDL module paths, resource paths).
- Usage: Passed into importer calls and surfaced in the options dialog.

### `SMDLOptionsWindow`

- Role: Slate dialog shown during import; allows users to confirm options, import, cancel, or access help.

### `FMDLMaterialSelector`

- Role: Classifies MDL materials (opaque, masked, translucent, carpaint, subsurface, clearcoat, emissive) and picks the correct UE material factory path.

## 4. Typical usage patterns

- Enable the plugin on desktop platforms and ensure MDL SDK binaries are present under `Plugins/Enterprise/MDLImporter/Binaries/ThirdParty/MDL/<Platform>`.
- Import `.mdl` files from the Content Browser; configure `UMDLImporterOptions` in the options dialog (module/resource paths, etc.).
- Use reimport to refresh materials; review the importer log for unsupported features (e.g., light profiles, measured BSDF/BTF textures).

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
