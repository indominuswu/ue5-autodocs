# RemoteSession Plugin Overview

## 1. What this plugin does
- Provides a thin-client/host system to mirror rendering and input between Unreal instances.
- Supports streaming images, input, AR/XR data, frame buffers, LiveLink, and recording via BackChannel transport.
- Includes editor UI for managing sessions and streaming.
- Experimental and disabled by default.

## 2. Key Modules
- **RemoteSession** (Runtime)
  - Role: Core networking/transport, roles (client/host), channels for image, input, AR/XR, LiveLink, recording, and media output.
  - Notable types: `RemoteSessionModule`, `RemoteSessionHost`, `RemoteSessionClient`, `RemoteSessionRole`, channels (`RemoteSessionImageChannel`, `RemoteSessionInputChannel`, `RemoteSessionARCameraChannel`, `RemoteSessionARSystemChannel`, `RemoteSessionXRTrackingChannel`, `RemoteSessionFrameBufferChannel`, `RemoteSessionLiveLinkChannel`), message handlers (`ProxyMessageHandler`, `RecordingMessageHandler`), media output providers.
- **RemoteSessionEditor** (Editor)
  - Role: Editor UI and styles for starting/managing sessions (`RemoteSessionEditorModule`, `SRemoteSessionStream`, `RemoteSessionEditorStyle`).

## 3. Important Types & APIs
### `IRemoteSessionRole` / `RemoteSessionRole`, `RemoteSessionHost`, `RemoteSessionClient`
- Role: Define the role of the instance (host or client) and manage channel lifecycles.

### Channel classes (e.g., `RemoteSessionImageChannel`, `RemoteSessionInputChannel`, `RemoteSessionFrameBufferChannel`, `RemoteSessionARCameraChannel`, `RemoteSessionLiveLinkChannel`)
- Role: Transport specific data types (frames, input, AR/XR data, LiveLink) over BackChannel.
- Key properties: quality/format settings, buffering, recording hooks.

### `RemoteSessionMediaOutput`, `RemoteSessionFrameBufferImageProvider`
- Role: Provide media/frame data to channels for streaming or recording.

### Editor UI (`SRemoteSessionStream`)
- Role: UI panel to monitor/launch remote sessions in the editor.

## 4. Typical usage patterns
- Enable the plugin and dependencies (BackChannel, AppleImageUtils, MediaIOFramework, XRBase, optional PixelStreaming2 in editor).
- In the host instance, start a session (via editor UI or code) exposing desired channels.
- In the client instance, connect using `RemoteSession` APIs; receive streamed frames and send input.
- Use recording handler to capture sessions, or AR/XR channels to mirror device data.

## 5. Version-specific notes (UE 5.7)
- Marked experimental in the `.uplugin`; tvOS is denied.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
