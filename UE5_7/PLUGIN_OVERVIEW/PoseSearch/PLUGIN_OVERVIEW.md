# Pose Search Plugin Overview

## 1. What this plugin does
- Provides a framework for indexing and searching pose features to power motion matching and related techniques.
- Builds searchable pose databases and exposes runtime queries for selecting best-matching animations.
- Includes editor tooling for database creation, schema authoring, and interactive debugging/visualization.

## 2. Key Modules
- **PoseSearch** (Runtime)  
  - Core runtime pose indexing/search, feature extraction, and interaction subsystem.  
  - Notable types: `UPoseSearchInteractionSubsystem`, pose search contexts, schema/database assets.
- **PoseSearchEditor** (UncookedOnly)  
  - Editor tools for authoring databases and schemas, plus debug UI.  
  - Notable types: `UPoseSearchDatabaseEdMode`, asset factories (`PoseSearchDatabaseFactory`, `PoseSearchSchemaFactory`, `PoseSearchInteractionAssetFactory`, `PoseSearchNormalizationSetFactory`), debugger settings (`PoseSearchDebuggerSettings`, `PoseSearchMeshComponent`).

## 3. Important Types & APIs

### `UPoseSearchInteractionSubsystem`
- Role: `UTickableWorldSubsystem` coordinating multi-character interaction motion matching; aggregates published `FPoseSearchInteractionAvailability` from anim instances and returns search results per character.
- Key behavior: processes availability, builds interaction islands, performs searches on worker threads, and exposes query helpers via `PoseSearchInteractionLibrary`.

### Pose search assets (schemas, databases, interaction assets)
- Role: Schemas define which pose features are indexed; databases store animations/feature vectors; interaction assets define multi-character participation data.

### Editor tooling (`UPoseSearchDatabaseEdMode`, factories, debugger settings)
- Role: Dedicated editor mode and factories to create/search/visualize pose databases; debugger settings control overlay/mesh components for inspecting results.

## 4. Typical usage patterns
- Enable the plugin along with dependencies (e.g., Animation Warping, BlendStack, Chooser as referenced in the plugin).
- Author a Pose Search Schema and Database via the Content Browser factories; populate the database with animations to index.
- At runtime, publish availability via `PoseSearchInteractionLibrary` from your anim instances; query `UPoseSearchInteractionSubsystem` to retrieve best matches for locomotion or interactions.
- Use the Pose Search editor mode and debugger settings to visualize feature spaces and debug query results while iterating.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
