# LiveLinkPrestonMDR Plugin Overview

## 1. What this plugin does

- Live Link source for Preston MDR-3 motor drivers used in virtual production focus/iris/zoom (FIZ) workflows.
- Publishes MDR lens telemetry as Live Link camera role data with configurable calibration or raw encoder input.
- Includes an editor source panel and factory to create/manage the Live Link source from the UI.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users add a Preston MDR source via the LiveLink UI/panel and configure data mode/encoder ranges to stream FIZ telemetry as LiveLink camera data.

## 3. Key Modules

- **LiveLinkPrestonMDR** (Runtime)
  - Role: Implements the Live Link source, data role, and data structs for Preston MDR streams.
  - Notable types: `ULiveLinkPrestonMDRSourceSettings`, `ULiveLinkPrestonMDRRole`, `FLiveLinkPrestonMDRSource`, `FPrestonMDRMessageThread`.
- **LiveLinkPrestonMDREditor** (Editor)
  - Role: Editor integration that exposes the Preston MDR Live Link source panel and factory for adding the source.
  - Notable types: `FLiveLinkPrestonMDREditorModule`, `SLiveLinkPrestonMDRSourcePanel`, `ULiveLinkPrestonMDRFactory`.

## 4. Important Types & APIs

### `ULiveLinkPrestonMDRSourceSettings`

- Role: Live Link source settings for MDR streams, selectable between raw encoder and calibrated FIZ data.
- Key properties: `IncomingDataMode` (`EFIZDataMode`), per-axis encoder ranges `FocusEncoderRange`, `IrisEncoderRange`, `ZoomEncoderRange`.

### `ULiveLinkPrestonMDRRole`

- Role: Live Link camera-derived role that defines static/frame/blueprint data layouts for MDR camera telemetry.
- Key functions: Overrides `GetStaticDataStruct`, `GetFrameDataStruct`, `GetBlueprintDataStruct`, and `InitializeBlueprintData` to map incoming MDR packets.

### `FLiveLinkPrestonMDRSource`

- Role: Live Link source implementation that connects to MDR, parses messages on a dedicated thread, and pushes Live Link subject data.
- Key behaviors: Applies `ULiveLinkPrestonMDRSourceSettings` (data mode and encoder ranges) and listens for settings changes to adjust scaling.

### `FPrestonMDRMessageThread`

- Role: Background thread that reads MDR network messages, parses FIZ values, and forwards them to the source.

## 5. Typical usage patterns

- Enable the plugin and open Live Link in the editor, then add a Preston MDR source via the provided source panel/factory.
- Choose the incoming data mode (raw encoder vs calibrated) and configure per-axis encoder ranges if using raw encoder data.
- Consume the Live Link subject as camera data in Control Rig, Sequencer, or other systems that read FIZ from Live Link camera roles.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

