# Datasmith Content Plugin Overview

## 1. What this plugin does

- Supplies core actors, components, templates, and metadata helpers used by Datasmith imports.
- Adds editor customizations for Datasmith asset types and import options.
- Provides Blueprint utilities to read/write Datasmith metadata and work with imported assets.
- Bundles supporting content (area lights, camera templates, decals, landscapes) used by Datasmith scenes.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Datasmith users work with these actors/templates and `UDatasmithContentBlueprintLibrary` to inspect metadata and adjust imported assets in editor/runtime.

## 3. Key Modules

- **DatasmithContent** (Runtime) – Runtime classes for Datasmith assets, templates, and helper actors.
- **DatasmithContentEditor** (Editor) – Details panels, asset definitions, and editor styles for Datasmith asset workflows.

## 4. Important Types & APIs

- `ADatasmithAreaLightActor` / `UDatasmithAreaLightActorTemplate` – Rect/disc/sphere area lights with Datasmith-controlled photometric settings.
- `UDatasmithAssetUserData` / `UDatasmithAdditionalData` – Metadata containers attached to imported actors/assets.
- `UDatasmithContentBlueprintLibrary` – Blueprint-callable helpers to query and modify Datasmith metadata on objects.
- `UDatasmithAssetImportData` / `UDatasmithImportOptions` – Persist import settings and source information for Datasmith assets.
- `ADatasmithImportedSequencesActor` – Helper actor for playing back imported level sequences.
- Template classes such as `UDatasmithCineCameraComponentTemplate`, `UDatasmithLandscapeTemplate`, and `UDatasmithDecalComponentTemplate` – Capture imported component settings for reapplication at runtime.

## 5. Typical usage patterns

- Enable alongside Datasmith Importer; imported Datasmith scenes will instantiate area lights, cine cameras, decals, and other template-driven components from this plugin.
- Use `UDatasmithContentBlueprintLibrary` to access Datasmith metadata in Blueprints (e.g., read custom key/value pairs stored on actors).
- Inspect and adjust Datasmith asset properties in the editor via the provided details customizations and asset definitions.
- Leverage `UDatasmithAssetImportData` to track source files and reimport Datasmith assets when source content changes.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

