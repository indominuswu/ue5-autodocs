# CineCameraSceneCapture Plugin Overview

## 1. What this plugin does

- Adds a cine-focused scene capture component that renders cine camera views to render targets.
- Mirrors the behavior of cine cameras in scene captures, including color management and view state controls.
- Designed for virtual production workflows requiring consistent capture output from cine cameras.

## 2. Key Modules

- **CineCameraSceneCapture** (Runtime)  
  - Role: Runtime scene capture component aligned with cine camera properties.
  - Notable types: `UCineCaptureComponent2D`.

## 3. Important Types & APIs

### `UCineCaptureComponent2D`
- Role: Scene capture component specialized for cine cameras; extends `USceneCaptureComponent2D`.
- Key properties: `RenderTargetHighestDimension` (resize target based on camera aspect), `bFollowSceneCaptureRenderPath`, `bOverrideUserFlags`/`UserFlags`, `FOpenColorIODisplayConfiguration` for color transforms, reference to target `UCineCameraComponent`.
- Overrides: `UpdateSceneCaptureContents`, `OnRegister` to sync with cine camera settings.

## 4. Typical usage patterns

- Attach `UCineCaptureComponent2D` to a `UCineCameraComponent` (or derived camera actor) to capture its view to a render target.
- Configure maximum render target dimension and choose whether to follow the scene capture render path or align more closely with viewport rendering.
- Apply OpenColorIO display configuration for color-managed captures; use user flags to drive material behavior per-view.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
