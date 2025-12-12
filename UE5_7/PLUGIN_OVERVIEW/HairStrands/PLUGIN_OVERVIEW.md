# Groom Plugin Overview

## 1. What this plugin does
- Implements runtime rendering, simulation, and caching for strand-based hair grooms.
- Provides import, editing, binding, and dataflow tooling for groom assets and hair cards.
- Integrates with Niagara via hair data interfaces and with Sequencer through groom cache tracks.
- Supplies physics/solver components and plugin-wide settings for hair rendering and simulation.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor grooming tools plus runtime components/Blueprint APIs for rendering and simulating hair.

## 3. Key Modules
- **HairStrandsCore** (Runtime)  
  - Role: Core asset types (groom assets, bindings, caches), rendering data, components, and Blueprint utilities.
- **HairStrandsDeformer** (Runtime)  
  - Role: Deformer support for groom data.
- **HairStrandsRuntime** (Runtime)  
  - Role: Runtime glue for groom playback and resource management.
- **HairStrandsSolver** (Runtime)  
  - Role: Runtime solver integration, including `UGroomSolverComponent` and cache adapters.
- **HairStrandsEditor** (Editor)  
  - Role: Importers, factories, editor modes, and asset toolkits for groom assets, bindings, caches, and cards.
- **HairCardGeneratorFramework** (Editor)  
  - Role: Editor framework helpers for hair card generation.
- **HairStrandsDataflow** (Editor)  
  - Role: Dataflow nodes for grooming workflows (guide building, resampling, spline skinning, attribute access).

## 4. Important Types & APIs

### Runtime assets & components
- `UGroomAsset`, `UGroomAssetCards`, `UGroomAssetMeshes`, `UGroomAssetPhysics`, `UGroomAssetRendering`: Core groom data and render/physics settings.
- `AGroomActor` / `UGroomComponent`: Actor/component for placing and rendering grooms in a level.
- `UGroomBindingAsset`, `UGroomBindingBuilder`: Bind grooms to skeletal meshes; includes helpers for generating bindings.
- `UGroomCache`, `UGroomCacheStreamingManager`: Store and stream baked groom animation.
- `UGroomBlueprintLibrary`: Blueprint helpers for creating bindings, follicle masks, and strand texture generation.
- `UGroomPluginSettings`: Project-wide defaults for rendering/simulation and feature toggles.

### Integration & simulation
- `UGroomCreateBindingOptions`, `UGroomCreateStrandsTexturesOptions`, `UGroomCreateFollicleMaskOptions`: Option structs for build helpers.
- `UGroomSolverComponent`, `UGroomCacheAdapter`: Runtime solver hookup for simulation/caching.
- Niagara: `UNiagaraDataInterfaceHairStrands`, `UNiagaraDataInterfaceVelocityGrid`, `UNiagaraDataInterfacePressureGrid` expose groom data to Niagara.
- Sequencer: `UMovieSceneGroomCacheTrack` / `UMovieSceneGroomCacheSection` for playing groom caches.

### Dataflow/editor tooling
- Dataflow nodes such as `UAttachGuidesRootsNode`, `UBuildGroomSplineSkinningNode`, `UBuildGuidesLODsNode`, `UGenerateGuidesCurvesNode`, `UResampleGuidesPointsNode`, `USmoothGuidesCurvesNode`, `UGroomAssetTerminalNode`, `UGetGroomAttributesNodes`.
- Editor factories/actions: `UGroomFactory`, `UGroomBindingFactory`, `UGroomCacheImporter`, `UGroomEditorMode`, `UGroomCustomAssetEditorToolkit`, viewport widget `SGroomEditorViewport`.

## 5. Typical usage patterns
- Editor: Enable the plugin, import hair data (e.g., Alembic) to create `GroomAsset`s, generate binding assets to skeletal meshes, and optionally bake groom caches. Use the Groom editor or Dataflow nodes for guide editing and card generation.
- Runtime: Place `GroomActor` or add a `GroomComponent` to an actor; assign groom and binding assets plus physics/render settings. Use groom caches for baked animation or `GroomSolverComponent` for simulation. Niagara systems can read groom data via the provided data interfaces.
- Sequencer: Add groom cache tracks to control playback timing of cached simulations.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
