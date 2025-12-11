# Procedural Vegetation Editor Plugin Overview

## 1. What this plugin does

- Node-graph-based editor for authoring Nanite-ready procedural vegetation assets entirely inside Unreal.
- Ships presets describing species data (meshes, growth, wind) and allows authoring variations via graph nodes.
- Generates vegetation outputs (meshes, LOD data, materials) suitable for foliage rendering workflows.
- Experimental and disabled by default.

## 2. Key Modules

- **ProceduralVegetation** (Runtime)  
  - Role: Core data types and graph runtime for procedural vegetation assets and presets.
  - Notable types: `UProceduralVegetation`, `UProceduralVegetationPreset`, `UProceduralVegetationLink`, data structs such as `UPVData`, `UPVMeshData`, `UPVGrowthData`, `UPVFoliageMeshData`.
- **ProceduralVegetationEditor** (Editor)  
  - Role: Editor UI, graph nodes, and asset authoring support for vegetation graphs.
  - Notable types: Blueprintable settings nodes like `UPVBaseSettings`, `UPVOutputSettings`, `UPVBoneReductionSettings`; editor graph utilities.

## 3. Important Types & APIs

### `UProceduralVegetation`

- Role: Root asset representing a vegetation graph definition.
- Key properties: Links to presets, graph node data, generation parameters.

### `UProceduralVegetationPreset`

- Role: Stores reusable, species-specific data (meshes, textures, metadata) used as a starting point for graph instances.
- Variants: A base class plus a BlueprintType derivative for authoring/editing.

### Settings/Data node classes (`UPVBaseSettings`, `UPVOutputSettings`, `UPVGrowthData`, `UPVMeshData`, `UPVFoliageMeshData`, `UPVWindSettings`)

- Role: BlueprintType node payloads that define growth, mesh assignment, wind response, and output targets.
- Usage: Instantiated inside the graph to drive generation; parameters exposed to the editor UI.

## 4. Typical usage patterns

- Enable the plugin and create a new Procedural Vegetation asset in the Content Browser.
- Load or assign a `UProceduralVegetationPreset` as a starting point, then edit the node graph (growth, mesh selection, wind, output settings).
- Generate vegetation assets for Nanite foliage; outputs can be consumed by foliage/instancing systems.
- Editor module provides the authoring experience; runtime module holds the data types referenced at cook time.

## 5. Version-specific notes (UE 5.7)

- Experimental in UE 5.7; off by default.
- No UE 5.7-specific deprecations were observed in source files.
