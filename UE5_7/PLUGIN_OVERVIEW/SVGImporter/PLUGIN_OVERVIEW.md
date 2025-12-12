# SVG Importer Plugin Overview

## 1. What this plugin does
- Imports SVG files into Unreal and converts vector shapes into dynamic mesh components.
- Provides runtime actors/components for SVG shapes (fill/stroke/combined meshes) and Blueprint/utility helpers.
- Editor module adds factories, reimport support, and component visualizers for SVG actors.
- Integrates with GeometryScripting/GeometryMask for vector-to-mesh processing.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Provides editor SVG import/reimport tooling and runtime actors/components for vector content.

## 3. Key Modules
- **SVGImporter** (Runtime, Beta) – Runtime SVG asset representation, dynamic mesh components, engine subsystem, and utilities for baking/joining shapes.
- **SVGImporterEditor** (Editor) – SVG asset factories (`USVGFactory`, `USVGReimportFactory`), actor factory, editor component visualizers, and tool/UI support.

## 4. Important Types & APIs
- `USVGImporterSettings` (`UDeveloperSettings`) – Runtime import/bake defaults.
- Actor/component types: `ASVGActor`, `ASVGJoinedShapesActor`, `ASVGShapeActor`, `ASVGShapesParentActor` hold SVG meshes and organize shape components.
- Dynamic mesh components: `USVGDynamicMeshComponent` (base), `USVGFillComponent`, `USVGStrokeComponent`, `UJoinedSVGDynamicMeshComponent`, `USVGBaseDynamicMeshComponent`.
- `USVGActorEditorComponent` – Editor-only component for manipulation/visualization.
- `USVGEngineSubsystem` (`UEngineSubsystem`) – Delegates for actor readiness, split events, and shape updates.
- Utilities: `USVGImporterUtils` (baking SVG meshes to static meshes, converting splines to polylines, joining/splitting shapes).
- Editor factories: `USVGFactory`/`USVGReimportFactory` for asset import, `USVGActorFactory` for spawning SVG actors.

## 5. Typical usage patterns
- Enable the plugin and import an `.svg` file; the editor factory creates SVG assets and associated actors with fill/stroke mesh components.
- Use the runtime actors/components to render SVG content; bake to static meshes via `USVGImporterUtils::BakeSVGDynamicMeshToStaticMesh`.
- Split or join SVG shapes using utilities (`CreateSVGJoinedActor`, `CreateSVGShapeActorFromShape`) to manage per-shape actors.
- Editor visualizers assist with manipulating spline/shape geometry; reimport updates actors via the editor module.

## 6. Version-specific notes (UE 5.7)
- Plugin is marked beta/experimental; no UE 5.7-specific changes beyond current functionality.
