# Legacy Composure Plugin Overview

## 1. What this plugin does
- Legacy real-time compositing system with a graph of compositing elements, captures, and post-process passes.
- Provides actors and Blueprint libraries for building compositing pipelines (captures, post-process blends, tonemapping).
- Editor tools and layer editor to manage compositing element collections and Sequencer integration.

## 2. Key Modules
- **Composure** (Runtime)  
  - Role: Compositing elements, capture components, pipeline actors, view extension, and Blueprint library.
- **ComposureEditor** (Editor)  
  - Role: Editor module for Composure tooling and Sequencer support.
- **ComposureLayersEditor** (Editor)  
  - Role: Layer/collection editor UI, view models, and detail customizations for compositing elements.

## 3. Important Types & APIs

### `UCompositingElement`
- Role: Core unit in the compositing graph; manages inputs, transforms, and rendering passes.
- Key properties: input passes, transform chain, output targets; supports layering and proxy rendering.

### `AComposurePipelineBaseActor`
- Role: Actor that owns a compositing pipeline; spawns and coordinates compositing elements in a level.

### `UComposureBlueprintLibrary`
- Role: Blueprint function library exposing helpers to manipulate compositing elements, frame transforms, and post-process utilities.

### Pass helpers
- `UComposureLensBloomPass`, `UComposurePostProcessPass`, `UComposureTonemapperPass`: Specific post-process implementations that can be inserted into a pipeline.
- `UCompositingCaptureBase`, `UComposurePlayerCompositingTarget`: Capture and output components for player-linked compositing.

### Editor-facing classes
- `FCompElementCollectionViewModel`, `FCompElementManager`, `FCompElementEditorModule`: Manage element collections and editor UI.
- Sequencer support under `ComposureEditor/Sequencer` for animating compositing parameters.

## 4. Typical usage patterns
- Editor: Create compositing elements, assemble them in a pipeline actor, and edit layers with the Composure Layers Editor. Use Sequencer tracks to animate element parameters. Blueprint nodes from `UComposureBlueprintLibrary` assist in updating transforms and passes.
- Runtime: Place a pipeline actor or spawn via Blueprint, configure passes and inputs, and render to targets visible in the viewport or external outputs.
- Migration: Marked as legacy; newer workflows may prefer newer compositing stacks, but this plugin remains available.

## 5. Version-specific notes (UE 5.7)
- Description labels the plugin as legacy; no new 5.7-specific changes are flagged in code. Overview reflects current sources.
