# Post Process Material Chain Graph Plugin Overview

## 1. What this plugin does

- Lets users stack multiple post-process materials into a graph and render them in order, optionally writing to custom render targets instead of scene color.
- Supports choosing when in the post-processing pipeline to execute (before post-process, after motion blur, after tone map, etc.).
- Provides an actor/component to run a graph in a level plus editor asset types/factories to author graphs.
- Experimental feature set for advanced compositing and render-target workflows.

## 2. Key Modules

- **PPMChainGraph** (Runtime)  
  - Role: Defines the `UPPMChainGraph` asset, execution component, actor, and world subsystem that runs graph instances.
  - Notable types: `UPPMChainGraph`, `UPPMChainGraphComponent`, `APP MChainGraphActor`, `UPPMChainGraphWorldSubsystem`.
- **PPMChainGraphEditor** (Editor)  
  - Role: Asset factories, actor factory, and asset definitions for authoring chain graph assets in the editor.
  - Notable types: `UPPMChainGraphFactoryNew`, `UActorFactoryPPMChainGraphActor`, `UAssetDefinition_PPMChainGraph`.

## 3. Important Types & APIs

### `UPPMChainGraph`

- Role: Asset describing a chain of post-process materials, their inputs (`EPPMChainGraphPPMInputId`), outputs (`EPPMChainGraphOutput`), and execution location (`EPPMChainGraphExecutionLocation`).
- Key properties: Material list, render-target names for intermediate outputs, execution stage selection, camera bindings.

### `UPPMChainGraphComponent`

- Role: Scene component that executes a chain graph at runtime or in PIE.
- Key properties: Graph asset reference, camera/target bindings, toggles for enabling execution.

### `APP MChainGraphActor`

- Role: Placeable actor that owns a `UPPMChainGraphComponent` for quick level placement.
- Usage: Drag into a level and assign a chain graph asset to drive post-process material execution.

### `UPPMChainGraphWorldSubsystem`

- Role: Manages registration and ticking of chain graph components within a world.
- Behavior: Ensures graphs execute at the configured post-processing stage and handles render-target routing.

## 4. Typical usage patterns

- In the editor, create a new Post Process Material Chain Graph asset via the content browser (factory) and add post-process materials in the desired order.
- Place a `PPMChainGraphActor` or add a `UPPMChainGraphComponent` to an existing actor; assign the graph asset and choose the execution stage (e.g., PrePostProcess, AfterToneMap).
- Optionally name render targets in graph nodes to collect intermediate outputs instead of writing back to scene color.
- Use the editor module tools to instantiate assets; runtime module handles execution with no additional Blueprint nodes required.

## 5. Version-specific notes (UE 5.7)

- Experimental; not enabled by default in UE 5.7.
- No explicit 5.7-specific deprecations were found; APIs reflect the current source snapshot.
