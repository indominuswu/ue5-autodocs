# Interchange Framework Plugin Overview

## 1. What this plugin does

- Core import/export framework providing translators, pipelines, and factory nodes for multiple asset types (meshes, animation, materials, audio, etc.).
- Implements dispatcher, messaging, and node containers to shuttle data between translators and factories.
- Ships with GLTF core, FBX parser, and common node definitions used by editor-facing tooling.
- Hidden but enabled by default because editor plugins depend on it.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Foundation for editor import/export; users configure translators/pipelines (FBX/GLTF), adjust `UInterchange*Settings`, and rely on the node/pipeline system during asset import.

## 3. Key Modules

- **GLTFCore** (Runtime) — Shared GLTF utilities.
- **InterchangeNodes** (Runtime, PreDefault) — Base node types for interchange graphs.
- **InterchangeFactoryNodes** (Runtime, PreDefault) — Factory node definitions for creating engine assets.
- **InterchangeImport** (Runtime, PreDefault) — Translators and import orchestration.
- **InterchangeMessages** (Runtime) — Messaging/result objects for translators/import.
- **InterchangeExport** (Runtime) — Export writer base and asset export helpers.
- **InterchangePipelines** (Runtime, PreDefault) — Pipeline base classes and generic asset pipelines.
- **InterchangeDispatcher** (Runtime) — Dispatch layer for parallelized import workers.
- **InterchangeCommon** / **InterchangeCommonParser** (Runtime) — Shared utilities and parsers.
- **InterchangeFbxParser** (Runtime, Editor/Program) — FBX parsing backend (Win64/Linux/Mac).

## 4. Important Types & APIs

### Core data & orchestration

- `UInterchangeBaseNodeContainer` — Graph container that holds translated nodes for assets and scenes.
- `UInterchangeSourceData` — Wraps a source file and its metadata for translators.
- `UInterchangeResult*` hierarchy — Import result/warning/error messaging used across modules.
- `UInterchangeDispatcher`/dispatcher helpers — Manage import tasks and worker processes.

### Translators & pipelines

- `UInterchangeTranslatorBase` with concrete implementations like `UInterchangeFbxTranslator`; paired with translator settings such as `UInterchangeFbxTranslatorSettings` and `UInterchangeVolumeTranslatorSettings`.
- `UInterchangePipelineBase` and generic pipelines (`UInterchangeGenericAssetsPipeline`, `UInterchangeGenericAnimationPipeline`, `UInterchangeGenericAudioPipeline`, `UInterchangeGenericMeshPipeline`, etc.) that process node containers into factory nodes and apply post-import logic.
- `UInterchangeFbxSettings` (DeveloperSettings) for project-level FBX import defaults.

### Factory nodes & asset writers

- Factory node hierarchy (`UInterchangeFactoryBaseNode`, `UInterchangeTextureFactoryNode`, `UInterchangeSkeletonFactoryNode`, `UInterchangeTextureLightProfileFactoryNode`, and other texture/material/mesh factory nodes) exposes asset properties to pipelines.
- Actor factories such as `UInterchangeStaticMeshActorFactory` and `UInterchangeSkeletalMeshActorFactory` apply node data to spawned actors.
- Export-side classes like `UInterchangeTextureWriter` support authoring interchange assets.

## 5. Typical usage patterns

- Editor-facing plugins (e.g., InterchangeEditor) invoke translators (FBX/GLTF/other) to populate a `UInterchangeBaseNodeContainer`.
- Configure pipelines (project defaults or user overrides) to decide how nodes become assets; pipelines create factory nodes and drive asset import.
- Translators expose per-format settings objects; project-level defaults come from `UInterchangeFbxSettings` and other translator settings.
- Variant and specialized pipelines can be registered to extend import behavior without modifying translators.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific flags were found; the plugin is enabled by default and marked non-experimental.

