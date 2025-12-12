# Water Plugin Overview

## 1. What this plugin does

- Experimental water system providing actors, components, and editor tools to author oceans, rivers, lakes, and custom water bodies.
- Generates water meshes/splines, flow data, collision, and buoyancy, plus landscape carving and caustics/brush utilities.
- Integrates with Niagara, Landmass, and GeometryProcessing for rendering and simulation.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor water authoring tools plus runtime water bodies, buoyancy, and Niagara data interfaces.

## 3. Key Modules

- **Water** (Runtime) – Core runtime components, water bodies, buoyancy, runtime settings, wave simulation, Niagara data interfaces, and water subsystems.
- **WaterEditor** (Editor) – Editor subsystem, spline/brush tools, actor factories, caustics generator, and visualization helpers.

## 4. Important Types & APIs

### Core runtime

- `UWaterSubsystem` (TickableWorldSubsystem): Manages global water state, water zones, and body registration.
- `UWaterRuntimeSettings` (DeveloperSettings): Project-wide defaults (water materials, collision toggles, default wave settings per body type).
- `UGerstnerWaterWaveSubsystem`: Engine subsystem for Gerstner wave data.

### Water bodies & splines

- Base `UWaterBodyComponent` (primitive component) with derived types: `UWaterBodyRiverComponent`, `UWaterBodyLakeComponent`, `UWaterBodyOceanComponent`, `UWaterBodyCustomComponent`.
- Actor counterparts: `AWaterBodyActor` base plus `AWaterBodyRiverActor`, `AWaterBodyLakeActor`, `AWaterBodyOceanActor`, `AWaterBodyCustomActor`, `AWaterBodyIslandActor`, `AWaterBodyExclusionVolume`.
- `UWaterSplineComponent` / `UWaterSplineMetadata`: Define body shape, flow, and depth along a spline.
- Mesh/rendering: `UWaterMeshComponent`, `UWaterBodyMeshComponent`, `UWaterBodyInfoMeshComponent`, `UWaterBodyStaticMeshComponent`.

### Simulation helpers

- `UBuoyancyComponent` and `UBuoyancyManager`: Buoyancy computation for actors interacting with water.
- Collision components: `UOceanCollisionComponent`, `UOceanBoxCollisionComponent`, `ULakeCollisionComponent`.
- Niagara: `UNiagaraWaterFunctionLibrary`, `UNiagaraDataInterfaceWater` to drive particle effects from water data.
- Shallow water: `UBakedShallowWaterSimulationComponent`.

### Editor tooling

- `UWaterEditorSubsystem`: Provides editor services for water authorship, brush operations, and spline visualization.
- `UWaterEditorSettings`: Editor-specific defaults for authoring.
- Brush/height tools: `UJumpFloodComponent2D`, `WaterBrushManager`, `WaterBodyActorFactory`, spline visualizers/details customizations; `ACausticsGeneratorActor` for caustics data.

## 5. Typical usage patterns

- Enable the Water plugin (and dependencies like Landmass/Niagara). Place water body actors (River/Lake/Ocean/Custom) and shape them with `WaterSplineComponent`.
- Configure global defaults in Project Settings → Water (materials, collision, wave presets). Adjust per-body properties (depth, flow, wave params, materials).
- Add `WaterZoneActor` to bound water meshes and manage streaming. Use `WaterMeshComponent` to render large bodies efficiently (Nanite-aware).
- Add `UBuoyancyComponent` to actors that should float, or use Niagara data interfaces for water-aware VFX.
- In editor, use WaterEditor brush tools to carve landscape, generate caustics, and build height/flow maps; spline visualizers assist with shaping rivers/coastlines.

## 6. Version-specific notes (UE 5.7)

- Plugin is marked experimental in 5.7; no additional UE 5.7-specific notes found beyond the current state in the source tree.
