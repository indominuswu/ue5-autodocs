# Capture Manager Core Plugin Overview

## 1. What this plugin does

- Supplies shared utilities and messaging used by the Capture Manager App and Capture Manager Editor plugins.
- Provides runtime capture helpers, protocol stacking, ingest core logic, and Live Link Hub capture messaging.
- Includes styling resources and take metadata definitions consumed by the Capture Manager UI.

## 2. Editor/Runtime surfaces

- User-facing: No - Provides shared capture utilities, messaging, and styles for other Capture Manager plugins but exposes no standalone editor panels or gameplay/runtime APIs.

## 3. Key Modules

- **CaptureUtils** (Runtime)  
  - Role: Core capture utilities and helper types needed at runtime.
- **CaptureProtocolStack** (Runtime)  
  - Role: Protocol stack and configuration helpers for ingest/capture data flow.
- **DataIngestCore** (Editor)  
  - Role: Editor-facing ingest logic and shared ingest tooling.
- **LiveLinkHubCaptureMessaging** (Editor)  
  - Role: Messaging layer for communicating between Live Link Hub and capture devices/endpoints.
- **CaptureManagerStyle** (Editor)  
  - Role: UI style resources for Capture Manager.
- **CaptureManagerTakeMetadata** (Editor)  
  - Role: Take metadata definitions used when importing or organizing captured takes.

## 4. Important Types & APIs

- Utility and messaging classes across the above modules provide the shared groundwork for ingest devices and UI elements; specific public-facing classes are defined per module (e.g., protocol stack helpers, messaging handlers).
- Take metadata definitions in `CaptureManagerTakeMetadata` module capture structured data about recorded content.

## 5. Typical usage patterns

- The plugin is automatically consumed by Capture Manager App/Editor; it does not expose its own UI.
- Ingest device modules rely on `CaptureProtocolStack` and `CaptureUtils` for protocol configuration and runtime helpers.
- Live Link Hub capture layouts use `LiveLinkHubCaptureMessaging` to talk to worker processes or devices.

## 6. Version-specific notes (UE 5.7)

- Plugin is disabled by default and acts as a dependency for other Capture Manager plugins in 5.7.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

