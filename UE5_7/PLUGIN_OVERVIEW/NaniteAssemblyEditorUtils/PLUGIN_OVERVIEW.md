# Nanite Assembly Editor Utilities Plugin Overview

## 1. What this plugin does
- Experimental tooling to build Nanite Assembly assets from static or skeletal mesh parts via Blueprints/editor scripts.
- Provides builder utilities for assembling meshes and handling material slot merging.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor-only Blueprint utilities for building Nanite Assembly assets.

## 3. Key Modules
- **NaniteAssemblyEditorUtils** (Editor)
  - Role: Editor-only utilities and Blueprint-facing builders for Nanite Assemblies.
  - Notable types: `UNaniteAssemblyBuilder`, `UNaniteAssemblyStaticMeshBuilder`, `UNaniteAssemblySkeletalMeshBuilder`.

## 4. Important Types & APIs

### `UNaniteAssemblyBuilder`
- Role: Core BlueprintType struct/class for constructing Nanite Assembly assets from parts.
- Key data: `FNaniteAssemblyMaterialMergeOptions` (merge behavior, slot group, overrides), `FNaniteAssemblyCreateNewParameters` (target directory/name/overwrite).
- Supports material slot grouping/merging strategies (`ENaniteAssemblyPartMaterialMerge`).

### `UNaniteAssemblyStaticMeshBuilder` / `UNaniteAssemblySkeletalMeshBuilder`
- Role: Specialized builders for static or skeletal mesh sources when generating Nanite Assemblies.

## 5. Typical usage patterns
- Enable the plugin (experimental) and call the builder classes from editor utilities or Blueprints to compose Nanite Assembly assets.
- Configure material merge options and target asset path via `FNaniteAssemblyCreateNewParameters`; supply parts via static/skeletal mesh builders.

## 6. Version-specific notes (UE 5.7)
- Plugin is experimental; no additional UE 5.7-specific notes found in source comments.
