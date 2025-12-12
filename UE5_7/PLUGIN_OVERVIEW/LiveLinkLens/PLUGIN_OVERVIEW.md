# LiveLinkLens Plugin Overview

## 1. What this plugin does
- Adds a LiveLink lens role and controller for streaming calibrated lens data (distortion, focus/zoom) into Unreal.
- Supports driving lens components and sequencer tracks with streamed lens metadata.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users attach `ULiveLinkLensController` to cameras/lens components to consume LiveLink lens role data and record/play it back in Sequencer.

## 3. Key Modules
- **LiveLinkLens** (Runtime)  
  - Role: LiveLink lens role/controller implementation and media types.
  - Notable types: `ULiveLinkLensController`, `LiveLinkLensRole`, `LiveLinkLensTypes`, `MovieSceneLiveLinkSubSectionLensRole`.

## 4. Important Types & APIs

### `ULiveLinkLensController`
- Role: `ULiveLinkControllerBase` derivative that applies lens role data to an attached component (e.g., lens component/camera).
- Key behavior: On evaluation, maps incoming lens role frame data to the target component; overrides desired component class and handles setup/cleanup when attached.
- Deprecated fields note that distortion/overscan now live on the lens component itself.

### `LiveLinkLensRole` / `LiveLinkLensTypes`
- Role: Define the LiveLink role and data structures used for lens streams (distortion, focus/zoom).

## 5. Typical usage patterns
- LiveLink panel: Add a source that publishes a Lens role; attach `ULiveLinkLensController` via a LiveLink component on the camera/lens actor to consume the stream.
- Sequencer: Use the LiveLink lens subsection types when recording or playing back lens data in sequences.
- Pair with the Lens Component plugin to apply distortion and nodal offsets using streamed lens calibration data.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; deprecated distortion fields remain for compatibility but are superseded by Lens Component handling.

