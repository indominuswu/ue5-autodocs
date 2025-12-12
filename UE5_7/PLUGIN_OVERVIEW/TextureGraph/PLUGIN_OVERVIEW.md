# TextureGraph Plugin Overview

## 1. What this plugin does

- Graph-based texture creation and manipulation tool focused on procedural workflows.
- Provides runtime graph evaluation plus editor tooling for building graphs, previewing results, and exporting textures.
- Includes insight modules for profiling/debugging graph execution.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Texture authoring toolset with graph assets/editor (`UTG_Graph`, TextureGraphEditor) and runtime evaluation for procedural/baked textures.

## 3. Key Modules

- **TextureGraphEngine** (Runtime)
  - Role: Core evaluation and engine-side utilities for running texture graphs.
- **TextureGraph** (Runtime)
  - Role: Public graph types (`TG_Graph`, `TG_Node`, pins, materials) and texture data structures used at runtime.
- **TextureGraphEditor** (Editor)
  - Role: Editor UI, exporters, details panels, and factories for graph assets and previews.
- **TextureGraphInsight / TextureGraphInsightEditor** (Editor)
  - Role: Insight/diagnostic tooling to inspect graph performance.

## 4. Important Types & APIs

### `UTG_Graph` and supporting types (`FTG_Node`, `FTG_Pin`, `FTG_Var`, `FTG_Signature`)

- Role: Represent a texture graph, its nodes, pins, and typed variables/signatures used during evaluation.

### `FTG_TextureDescriptor` / `FTG_Texture`

- Role: Describe output resolution/format/sRGB and wrap tiled texture blobs produced by the graph; convertible to buffer descriptors.

### `TG_OutputSettings` and evaluation helpers

- Role: Configure outputs during evaluation (formats, LODs, export options) and provide utility hashing/logging helpers.

### Editor assets and exporters

- Role: `TG_Exporter` and related UI spawn tabs for preview/export settings; `TG_ExportSettings` and preview scene settings drive export targets.

## 5. Typical usage patterns

- Enable the plugin, create a Texture Graph asset, and edit nodes in the Texture Graph editor to assemble procedural textures.
- Use the preview and export tabs to visualize results and write baked textures; adjust `TG_OutputSettings` to control resolution/format.
- Integrate runtime evaluation via `UTG_Graph` APIs to procedurally generate textures in tools or cook-time workflows.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

