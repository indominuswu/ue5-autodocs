# Datasmith Interchange Plugin Overview

## 1. What this plugin does

- Bridges Datasmith content into the Unreal Interchange pipeline.
- Supplies Interchange pipelines, factories, and material selectors tailored for Datasmith scenes.
- Reuses Datasmith reference material selectors for multiple DCC sources inside Interchange.

## 2. Key Modules

- **DatasmithInterchange** (Runtime) – Interchange pipelines, nodes, and material selectors for Datasmith content.

## 3. Important Types & APIs

- `UInterchangeDatasmithPipeline` – Top-level pipeline that configures Datasmith-specific import steps.
- `UInterchangeDatasmithLevelPipeline` – Handles Datasmith level/actor import inside the Interchange framework.
- `UInterchangeDatasmithStaticMeshPipeline` and `UInterchangeDatasmithMaterialPipeline` – Process mesh and material data from Datasmith payloads.
- `UInterchangeDatasmithAreaLightFactory` / `UInterchangeDatasmithAreaLightNode` – Create Datasmith area light assets within Interchange.
- Material selector helpers such as `FDatasmithC4DMaterialSelector`, `FDatasmithCityEngineMaterialSelector`, `FDatasmithRevitMaterialSelector`, and `FDatasmithSketchupMaterialSelector` – Choose reference materials appropriate to the source DCC.
- Support types like `UInterchangeDatasmithStaticMeshData` and `UInterchangeDatasmithTextureData` – Carry translated mesh and texture data through the pipeline.

## 4. Typical usage patterns

- Enable Interchange and Datasmith Interchange, then import Datasmith payloads through the Interchange framework; select the Datasmith pipelines when prompted.
- Customize material selection using the provided selectors to align with source DCC conventions.
- Use the area light factory/node to retain Datasmith lighting when importing scenes via Interchange.
- Pipelines output standard Unreal assets (meshes, materials, lights) while preserving Datasmith metadata through Interchange nodes.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
