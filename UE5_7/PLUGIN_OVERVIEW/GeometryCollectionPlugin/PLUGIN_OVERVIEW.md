# Geometry Plugin Overview

## 1. What this plugin does

- Implements Geometry Collection authoring and playback for Chaos-based destruction workflows.
- Supplies extensive Dataflow node libraries for building and manipulating Geometry Collection data (creation, fracturing, clustering, materials, sampling).
- Adds editor tooling (asset factories, selection/edit modes, thumbnail/asset definitions) and Sequencer tracks for Geometry Collections.
- Provides example geometry and nodes for generating/processing collections.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Geometry Collection Dataflow nodes, Sequencer tracks, and editor factories/modes for Chaos destruction authoring.

## 3. Key Modules

- **GeometryCollectionEditor** (Editor)  
  - Role: Editor UI, factories, commands, selection mode, and asset definitions for Geometry Collections and caches.  
  - Notable types: `UGeometryCollectionFactory`, `UAssetDefinition_GeometryCollection`, `UGeometryCollectionCacheFactory`, `FGeometryCollectionSelectRigidBodyEdMode`, `FGeometryCollectionCommands`, thumbnail renderers, actor factories.

- **GeometryCollectionTracks** (Runtime)  
  - Role: MovieScene track/section types to animate Geometry Collection caches in Sequencer.  
  - Notable types: `UMovieSceneGeometryCollectionTrack`, `UMovieSceneGeometryCollectionSection`, `FMovieSceneGeometryCollectionTemplate`.

- **GeometryCollectionSequencer** (Editor)  
  - Role: Sequencer track editor integration for the Geometry Collection MovieScene track.  
  - Notable types: `FGeometryCollectionTrackEditor`.

- **GeometryCollectionNodes** (Runtime)  
  - Role: Dataflow node set for authoring/manipulating Geometry Collections (fracturing, clustering, conversion, sampling, utility nodes).  
  - Notable types: node headers such as `GeometryCollectionFracturingNodes`, `GeometryCollectionMakeNodes`, `GeometryCollectionFieldNodes`, `GeometryCollectionSamplingNodes`, `GeometryCollectionMeshNodes`, `GeometryCollectionMaterialNodes`, `GeometryCollectionSelectionNodes`.

- **GeometryCollectionDepNodes** (Runtime)  
  - Role: Dependent Dataflow nodes for vertex transfer and color utilities (e.g., `GeometryCollectionTransferVertexScalarAttributeDepNode`).  

## 4. Important Types & APIs

### Editor factories and commands

- `UGeometryCollectionFactory`, `UGeometryCollectionCacheFactory`, `UActorFactoryGeometryCollection` create assets/actors for collections and caches.
- `FGeometryCollectionCommands`/`FGeometryCollectionSelectionCommands` register toolbar/menu actions for collection editing.

### Dataflow node suites (`GeometryCollection*Nodes`)

- Role: Large node libraries for building collections: import/convert meshes, fracture (Voronoi, clustering, mesh-based), embed materials, sample/transfer attributes, generate fields, and perform selection/utility operations.
- Nodes are organized by topic (fracturing, clustering, materials, sampling, overrides, embedding, skeletal/static mesh conversion).

### Sequencer track types

- `UMovieSceneGeometryCollectionTrack` & section/template classes wrap playback of Geometry Collection caches inside Level Sequences.

### Editor mode

- `FGeometryCollectionSelectRigidBodyEdMode` provides viewport selection/editing of collection rigid bodies.

## 5. Typical usage patterns

- Enable the plugin along with dependencies (Chaos, Dataflow, Fracture). Create a Geometry Collection asset via the factory or convert meshes using Dataflow nodes.
- Use the editor commands/modes to fracture, cluster, and preview destruction setups; thumbnail and asset definition integrate with Content Browser.
- Author Dataflow graphs using the provided node libraries to procedurally generate or post-process Geometry Collections.
- In Sequencer, add a Geometry Collection track to play back a recorded/simulated cache against collection actors.

## 6. Version-specific notes (UE 5.7)

- The plugin is marked beta/experimental in the descriptor; no additional UE 5.7-specific notes surfaced.
