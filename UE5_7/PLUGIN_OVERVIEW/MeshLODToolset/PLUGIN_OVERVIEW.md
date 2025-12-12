# Mesh LOD Toolset Plugin Overview

## 1. What this plugin does
- Editor toolset for generating and managing static mesh LODs through graph-driven processes.
- Provides assets and tools to author reusable LOD generation settings and run batch LOD creation.
- Integrates with the Modeling tools pipeline with detail customizations and asset definitions.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor LOD generation tools, settings assets, and toolkits for static meshes.

## 3. Key Modules
- **MeshLODToolset** (Editor)
  - Role: Hosts LOD generation tools, process graphs, settings factories, and editor UI.
  - Notable types: `FMeshLODToolsetModule`, `ULODGenerationSettingsAsset`, `ULODGenerationSettingsFactory`, `UGenerateStaticMeshLODAssetTool`, `ULODManagerTool`, `UGenerateMeshLODGraph`, `UGenerateStaticMeshLODProcess`, `UAssetDefinition_StaticMeshLODGenerationSettings`.

## 4. Important Types & APIs
### `ULODGenerationSettingsAsset`
- Role: Data asset storing LOD generation recipes (reducers, simplification rules, bake options) that tools consume.

### `UGenerateStaticMeshLODAssetTool`
- Role: Interactive tool that executes a `UGenerateMeshLODGraph` against selected static meshes to produce LODs.
- Key properties: input mesh selections, target LOD levels, reference to `ULODGenerationSettingsAsset`.

### `ULODManagerTool`
- Role: Editor tool to inspect and manage existing LODs on selected meshes, including preview and replacement operations.

### `UGenerateMeshLODGraph` / `UGenerateStaticMeshLODProcess`
- Role: Graph/process definitions that orchestrate mesh reductions and bake steps used by the LOD tools.

## 5. Typical usage patterns
- Enable the plugin. Create a `LOD Generation Settings` asset via Content Browser (factory provided).
- In the Modeling/LOD tools, run `Generate Static Mesh LOD` to apply the settings asset to selected meshes.
- Use `LOD Manager` to review generated LODs, re-run processes, or swap settings assets.
- Asset definition integrates with asset picker and provides details panel customizations for settings assets.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; functionality matches the UE 5.7 source.
