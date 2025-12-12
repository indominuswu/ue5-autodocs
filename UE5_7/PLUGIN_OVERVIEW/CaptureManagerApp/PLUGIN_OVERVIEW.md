# Capture Manager Application Plugin Overview

## 1. What this plugin does

- Provides the Capture Manager layout for Live Link Hub to control ingest devices, monitor status, and manage captured takes.
- Includes ingest pipeline utilities, data conversion, media read/write helpers, and endpoints for Unreal-based capture.
- Ships metadata modules (Live Link Face, stereo camera) so captured media is tagged for downstream ingest.
- Example ingest devices are included for Live Link and network-based capture flows.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Capture Manager UI runs inside Live Link Hub for configuring ingest devices and take management; exposes settings objects and device factories users configure in editor tooling.

## 3. Key Modules

- **CaptureManagerEditor** (Editor)  
  - Role: Live Link Hub UI, ingest job orchestration, capture device scripting, and take management panels.
- **LiveLinkFaceMetadata**, **StereoCameraMetadata** (Editor)  
  - Role: Metadata providers for captures (face, stereo camera).
- **CaptureManagerPipeline**, **CaptureManagerMediaRW**, **CaptureDataConverter** (Editor)  
  - Role: Pipeline stages, media read/write, and conversion utilities used during ingest.
- **CaptureManagerUnrealEndpoint** (Editor)  
  - Role: Manages communication with Unreal endpoints used by the capture flow.
- **CaptureManagerSettings** (Editor)  
  - Role: Developer settings and tokens for capture configuration.
- **LiveLinkCapabilities**, **IngestLiveLinkDevice** (Editor)  
  - Role: Capability discovery and Live Link ingest device implementations.

## 4. Important Types & APIs

- `UCaptureManagerSettings` (CaptureManagerSettings module)  
  - Role: Developer settings storing general/audio/video encoder token configuration for capture workflows.
- `UIngestJobSettings` (CaptureManagerEditor module)  
  - Role: Defines ingest job parameters for processing captured data inside Live Link Hub.
- `ULiveLinkHubCaptureDevice` / `ULiveLinkHubCaptureDeviceFactory`  
  - Role: Factory and device definitions exposed to Live Link Hub capture layout.
- `UExampleNetworkIngestDeviceSettings` (ExampleLiveLinkDevices module)  
  - Role: Sample settings for network ingest device demonstrating how devices register with the pipeline.

## 5. Typical usage patterns

- Enable the plugin and open the Capture Manager layout in Live Link Hub to register ingest devices and monitor capture status.
- Configure project-level capture defaults in `CaptureManagerSettings`, including encoder token values.
- Create ingest jobs via the Capture Manager UI; jobs use `UIngestJobSettings` to define inputs and outputs.
- Use provided device modules (e.g., network ingest example, Live Link ingest) to route live or archived media into Unreal for conversion and take creation.

## 6. Version-specific notes (UE 5.7)

- Plugin ships only Editor-type modules in this 5.7 tree and is disabled by default.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

