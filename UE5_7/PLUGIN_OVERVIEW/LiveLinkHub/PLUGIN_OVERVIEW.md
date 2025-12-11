# Live Link Hub Plugin Overview

## 1. What this plugin does
- Hosts the standalone/editor Live Link Hub application for aggregating and routing Live Link devices and subjects (including UEFN workflows).
- Provides UI, settings, and messaging support for configuring hub sessions, recording, and timecode/synchronization.
- Adds runtime messaging module to publish hub data over the message bus for connected editors/clients.

## 2. Key Modules
- **LiveLinkHub** (EditorAndProgram)  
  - Core hub app logic, components, settings, and recording/playback helpers.  
  - Notable types: `ILiveLinkHubComponent`, `LiveLinkHubSettings`, `LiveLinkHubTimeAndSyncSettings`, `LiveLinkHubCustomTimeStepSettings`, `SLiveLinkHubSettings`.
- **LiveLinkHubEditor** (Editor)  
  - Editor-only settings integration (`LiveLinkHubEditorSettings`) and UI customizations for running the hub from the editor.
- **LiveLinkHubMessaging** (Runtime)  
  - Message bus source support for hub sessions.  
  - Notable types: `LiveLinkHubMessageBusSourceSettings`, `LiveLinkHubMessagingSettings`, `LiveLinkHubMessageBusSourceFactory`.

## 3. Important Types & APIs

### `ILiveLinkHubComponent`
- Role: Interface implemented by hub components so they can be discovered/managed by the hub application.

### `LiveLinkHubSettings` / `LiveLinkHubTimeAndSyncSettings` / `LiveLinkHubTimecodeSettingsCustomization`
- Role: Per-hub configuration for recording locations, default devices, custom time step, and timecode/clock sync behavior; exposed via details customizations.

### `LiveLinkHubPlaybackSourceFactory` / `LiveLinkHubPlaybackSourceSettings`
- Role: Factories/settings for creating playback sources inside the hub to review recorded sessions.

### `LiveLinkHubMessageBusSourceSettings` / `LiveLinkHubMessagingSettings`
- Role: Configure how the hub publishes/consumes subjects over the message bus to connected Unreal clients.

## 4. Typical usage patterns
- Run the Live Link Hub program (or enable the plugin inside the editor) to manage devices and stream subjects to Unreal/UEFN.
- Configure recording/output folders, timecode providers, and synchronization via the hub settings panels (`SLiveLinkHubSettings`).
- Add message bus sources for publishing data to connected editors; adjust messaging settings for network reachability.
- Use playback source factories to replay recorded sessions for validation.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
