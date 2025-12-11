# VirtualCameraCore Plugin Overview

## 1. What this plugin does

- Core runtime for Virtual Camera workflows: provides the `UVCamComponent`, modifier stack system, output providers, and input subsystems.
- Integrates with Enhanced Input, LiveLink, Pixel Streaming, Media IO, and Multi-User for remote camera control.
- Supplies editor customizations and Blueprint nodes that expose VCam control to designers.

## 2. Key Modules

- **VCamCore** (Runtime) – Main runtime (component, modifiers, subsystems, output providers, widget bindings).
- **DecoupledOutputProvider** (Runtime) – Output provider implementations decoupled from the VCam actor (e.g., render/stream widgets).
- **VCamCoreEditor** (Editor) – Details customizations, asset user data, and editor tooling for VCam assets.
- **VCamBlueprintNodes** (UncookedOnly) – Blueprint node wrappers for VCam APIs.
- **PixelStreamingVCam** (UncookedOnly) – Pixel Streaming integration (signaling, live link source settings) for remote VCam feeds.

## 3. Important Types & APIs

### `UVCamComponent`

- Role: Core controller attached to a `UCineCameraComponent`; manages modifier stacks, output providers, input routing, and connection points to widgets.
- Key concepts:
  - Modifiers (`UVCamModifier` and derivatives) adjust camera properties and expose Enhanced Input actions/connection points.
  - Output providers (`UVCamOutputProviderBase` and subclasses) render/stream UI widgets; can be configured via connection structs.
  - Subsystems: auto-instanced while the component is active, e.g. `UInputVCamSubsystem` (input binding), `UVCamSubsystem` base for custom extensions.
  - Events: `FOnComponentReplaced` fired when reconstruction replaces the component in-editor.

### `UVCamSubsystem` / `UInputVCamSubsystem`

- Role: Subsystem base living within a VCam component’s lifetime; `UInputVCamSubsystem` mirrors player-controller style input binding for VCams.
- APIs: `OnUpdate` tick hook, access to owning `UVCamComponent`, helper methods for binding input devices to modifier connection points.

### Pixel Streaming & remote control

- `UVCamPixelStreamingSubsystem`, signaling helpers, and `UPixelStreamingLiveLinkSourceSettings` enable streaming VCam output and LiveLink data to remote devices.
- Decoupled output providers can be swapped/instanced without altering the core actor.

### Utility APIs

- `UWidgetReferenceBlueprintFunctionLibrary` and blueprint nodes to manage widget references and prompt strings (`UPromptClientForStringAsyncAction`).
- View target policies (`UGameplayViewTargetPolicy`) to drive camera possession from VCams.

## 4. Typical usage patterns

- Attach `UVCamComponent` as a child of a `UCineCameraComponent` on a VCam actor. Configure modifiers (input mapping) and output providers (in-viewport, remote stream, etc.).
- Bind inputs through `UInputVCamSubsystem` or Enhanced Input assets; use connection points to wire widgets to modifier actions.
- For remote streaming, enable PixelStreamingVCam and configure signaling/server endpoints; optional LiveLink output for camera data.
- Use editor tools (VCamCoreEditor) to adjust details panels, add blueprint nodes, and store asset user data with VCam presets.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
