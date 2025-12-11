# Composure (Composite) Plugin Overview

## 1. What this plugin does
- Modern real-time compositing system succeeding legacy Composure and extending CompositeCore.
- Provides runtime components for scene capture, projection, and compositing meshes/shadows into final output.
- Includes editor actor factories to quickly place composite actors in a level.

## 2. Key Modules
- **Composite** (Runtime)  
  - Runtime compositing components and utilities.  
  - Notable types: `UCompositeSceneCapture2DComponent`, `UCompositeMeshComponent`, `UCompositeViewProjectionComponent`, `UCompositeShadowReflectionCatcherComponent`.
- **CompositeEditor** (Editor)  
  - Editor actor factories and tooling.  
  - Notable type: `CompositeActorFactory`.

## 3. Important Types & APIs

### `UCompositeSceneCapture2DComponent`
- Role: Specialized `USceneCaptureComponent2D` used in compositing pipelines; custom view owner handling for composure shots.

### `UCompositeMeshComponent`
- Role: Mesh component used for compositing surfaces/planes within the composite.

### `UCompositeViewProjectionComponent`
- Role: Handles view/projection setup for composite shots; aligns captured imagery with scene geometry.

### `UCompositeShadowReflectionCatcherComponent`
- Role: Captures or renders shadow/reflection contributions for composited elements.

### `CompositeActorFactory`
- Role: Editor factory to spawn composite actors with the appropriate components pre-configured.

## 4. Typical usage patterns
- Enable the plugin (Compositing category). Add composite actors via the provided actor factory or by placing components manually.
- Use `UCompositeSceneCapture2DComponent` to capture layers/passes, project them with `UCompositeViewProjectionComponent`, and render onto meshes via `UCompositeMeshComponent`.
- Employ `UCompositeShadowReflectionCatcherComponent` when capturing or inserting elements that require shadow/reflection integration.
- Combine with CompositeCore/Composure tools and Sequencer to build real-time comp shots.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
