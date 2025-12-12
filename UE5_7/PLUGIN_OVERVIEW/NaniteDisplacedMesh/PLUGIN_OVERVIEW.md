# Nanite Displaced Mesh Plugin Overview

## 1. What this plugin does
- Adds Nanite Displaced Mesh assets/components that pre-bake displacement into Nanite meshes.
- Provides editor tooling to create displaced meshes from static meshes and displacement maps, plus a generation commandlet.
- Supports component usage for placing displaced meshes in levels.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime displaced mesh assets/components with editor factories and generation tools.

## 3. Key Modules
- **NaniteDisplacedMesh** (Runtime)
  - Role: Runtime asset/component definitions and displacement parameters.
  - Notable types: `UNaniteDisplacedMesh`, `UNaniteDisplacedMeshComponent`, displacement params (`FNaniteDisplacedMeshParams`, `FNaniteDisplacedMeshDisplacementMap`), algorithms/logging helpers.
- **NaniteDisplacedMeshEditor** (Editor)
  - Role: Editor asset factories, customizations, and commandlet for generating displaced meshes.
  - Notable types: `UNaniteDisplacedMeshFactory`, `UNaniteDisplacedMeshEditorSubsystem`, `FAssetTypeActions_NaniteDisplacedMesh`, `GenerateNaniteDisplacedMeshCommandlet`, details customization classes.

## 4. Important Types & APIs

### `UNaniteDisplacedMesh`
- Role: Asset holding base mesh reference, displacement maps, and quality settings (`RelativeError`).
- Key data: array of `FNaniteDisplacedMeshDisplacementMap` (texture, magnitude, center), async compile support, equality checks for build caching.

### `UNaniteDisplacedMeshComponent`
- Role: Scene component that renders a displaced Nanite mesh asset.
- Usage: attach to actors to display the generated displaced mesh at runtime.

### Editor helpers
- Factories and asset type actions for creating assets; customization classes for details panel editing.
- `UNaniteDisplacedMeshEditorSubsystem` and the `GenerateNaniteDisplacedMeshCommandlet` support batch generation.

## 5. Typical usage patterns
- Enable the plugin (experimental) and import a static mesh plus displacement maps; create a Nanite Displaced Mesh asset via the factory or commandlet.
- Adjust displacement parameters (`Magnitude`, `Center`, `RelativeError`) and regenerate if needed.
- Place a `NaniteDisplacedMeshComponent` in the level or attach it to an actor to render the displaced asset.

## 6. Version-specific notes (UE 5.7)
- Plugin is experimental; no additional UE 5.7-specific notes found in source comments.
