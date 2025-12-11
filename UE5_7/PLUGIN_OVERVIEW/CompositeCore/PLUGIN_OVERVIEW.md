# CompositeCore Plugin Overview

## 1. What this plugin does
- Core runtime for real-time compositing holdout workflows using a post-process pipeline.
- Adds a holdout component that can be attached to actors to define alpha masks for downstream compositing.
- Provides a scene view extension and configurable settings to drive the compositing pass.

## 2. Key Modules
- **CompositeCore** (Runtime)  
  - Role: Implements the holdout component, settings asset, subsystem, and scene view extension that injects the holdout composite pass.

## 3. Important Types & APIs

### `UHoldoutCompositeComponent`
- Role: Component that marks actors for holdout compositing; supplies mask parameters to the view extension.
- Key properties: mask priority/weight and render target hooks.

### `UCompositeCoreSubsystem`
- Role: Subsystem coordinating holdout components and the compositing pass; registers view extensions and updates render data each frame.

### `UCompositeCoreSettings`
- Role: Configurable settings for the CompositeCore pipeline (mask render target options, cvars, and default parameters).

### `FCompositeCoreSceneViewExtension`
- Role: Scene view extension that renders the holdout pass into the composite pipeline.

## 4. Typical usage patterns
- Editor/runtime: Add `Holdout Composite` component to actors that should occlude or matte during compositing. Configure priorities in `Composite Core` project settings if needed.
- Rendering: Ensure the plugin is enabled; the subsystem registers the view extension automatically and renders holdouts during post-processing.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; functionality matches the current plugin sources.

