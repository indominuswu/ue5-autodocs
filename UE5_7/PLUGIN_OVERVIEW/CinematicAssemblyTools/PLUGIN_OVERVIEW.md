# Cinematic Assembly Tools (CAT) Plugin Overview

## 1. What this plugin does

- Provides shot/sequence management tooling for linear content and virtual production pipelines.
- Defines Cine Assembly assets and schemas plus production settings for organizing shots and folders.
- Integrates with Take Recorder and Sequencer for naming, metadata, and production workflows.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor asset factories/customizations and runtime helpers for Cine Assembly assets and production settings.

## 3. Key Modules

- **CineAssemblyTools** (Runtime)  
  - Role: Core asset definitions and runtime support for Cine Assembly data.
  - Notable types: `UCineAssembly`, `UCineAssemblySchema`, `FCineAssemblyNamingTokens`.
- **CineAssemblyToolsEditor** (Editor)  
  - Role: Editor UI, factories, analytics, and production settings for CAT.
  - Notable types: `UCineAssemblyFactory`, `UCineAssemblySchemaFactory`, `UAssetDefinition_CineAssembly`, `UAssetDefinition_CineAssemblySchema`, `UProductionSettings`, `UProductionFunctionLibrary`, `UCineAssemblyTakeRecorderSettings`, customizations (`CineAssemblyCustomization`, `CineAssemblySchemaCustomization`, `ProductionSettingsCustomization`), commands/styles.

## 4. Important Types & APIs

### Cine Assembly assets
- `UCineAssembly` / `UCineAssemblySchema`: Represent assembly data and schema for cinematic shots; naming tokens defined in `FCineAssemblyNamingTokens`.
- Factories (`UCineAssemblyFactory`, `UCineAssemblySchemaFactory`) and asset definitions register these assets in the editor.

### Production settings and utilities
- `UProductionSettings` (`DeveloperSettings`): Stores production folder templates, subsequence priority (`ESubsequencePriority`), and related defaults; broadcasts production change delegates.
- `UProductionFunctionLibrary`: Blueprint/utility functions for working with production data.
- `UCineAssemblyTakeRecorderSettings`: Integrates assemblies with Take Recorder.

### Editor tooling
- Customizations and styles for assembly/schema editors (`CineAssemblyCustomization`, `CineAssemblySchemaCustomization`, `CineAssemblyToolsStyle`).
- Analytics and commands (`CineAssemblyToolsAnalytics`, `CineAssemblyToolsEditorModule`) for editor workflow integration.

## 5. Typical usage patterns

- Enable CAT, create Cine Assembly and Schema assets via the provided factories/asset definitions.
- Configure `UProductionSettings` to define folder templates, subsequence priorities, and naming conventions for shots.
- Use the editor customizations to author assemblies, apply schemas, and integrate with Take Recorder for shot capture.
- Call utilities from `UProductionFunctionLibrary` in Blueprints or tools to query/update production data.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
